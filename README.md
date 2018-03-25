# Folium-Choropleth---Brazil-state
# Do choropleth map of brazilian state using folium librabry - python

geo_path = 'C:/Users/Rafael/Documents/Python Scripts/br-states.json'

geo_str = json.dumps(json.load(open(geo_path, 'r')))
threshold_scale = np.linspace(new_data['QTY'].min(),
                              new_data['QTY'].max(), 6, dtype=int).tolist()
                              
new_data = pd.DataFrame(values.items(), columns=['State','QTY'])

mapa = folium.Map(location=[-15.80, -47.88],
                  tiles="Mapbox Bright",
                  zoom_start=3)

folium.GeoJson(geo_str=geo_str,
               data=new_data,
               columns=['State', 'QTY'],
               fill_color='YlGn',
               key_on='feature.id',
               threshold_scale=threshold_scale).add_to(mapa)

mapa
    

mapa.save('index.html')
