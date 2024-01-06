import folium

m = folium.Map(
    location=[25.10, 121.59],  #緯度,經度
    zoom_start=12,
    tiles='Stamen Terrain'
)

fn2 = 'latitude.txt'
str1_1 = '25.1020'
str1_2 = '121.59'
str2_1 = '25.1015'
str2_2 = '121.59'
str3_1 = '25.1010'
str3_2 = '121.59'
str4_1 = '25.0471'
str4_2 = '121.5087'
str5_1 = '25.1060'
str5_2 = '121.5148'
place = 0
kevin = 0.0
mark = 0.0
marker = []
i = 0
while(place < 5):
    with open(fn2, 'r+') as file_obj:
        #file_obj.write(str2 + '\n')  #將經度寫入記事本

        for line in file_obj:
            marker.append(float(line.rstrip()))


    folium.Marker(  #標記符號
        location=[marker[i], marker[i+1]],
        popup='jack_handsome',
        icon=folium.Icon(color='red', icon='info-sign')
    ).add_to(m)
    i = i + 2
    place = place + 1
    m.save('index.html')

