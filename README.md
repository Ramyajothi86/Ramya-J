#importing Data set 
df = pd.read_csv('train.csv')

#Assigning R variable for radians 
R=6373.0

#declaring the cloumns to calculate 
lon1 = np.radians(df.iloc[:,3:4].values) 
lat1 = np.radians(df.iloc[:,4:5].values) 
lon2 = np.radians(df.iloc[:,5:6].values) 
lat2 = np.radians(df.iloc[:,6:7].values)

#Calculation 
dlon=lon2 - lon1 print(dlon)
dlat=lat2-lat1 print(dlat)
a = np.sin(dlat / 2)**2 + np.cos(lat1) * np.cos(lat2) * np.sin(dlon / 2)**2 print(a)
c = 2 * np.arctan2(np.sqrt(a), np.sqrt(1 - a)) 
print(c)

#output 
distance =R*c 
print(distance)

#sample outpt 
[[1.03108752e+00] [8.45278628e+00] [1.38996143e+00] [2.80014899e+00] [1.99978437e+00]

#Exporting the Output in CSV file 
df1=pd.DataFrame(distance) 
df1.to_csv('uberprice_out.csv')
