```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import numpy
```


```python
#LEYENDO EXCEL Y FILTRANDO EXCEL DE CENTRALES EN OPERACIÓN
df = pd.read_excel("Centrales_en_operación.xlsx")
df.drop("ID,N,16,6", axis="columns", inplace=True)
df = df[df.Energía == "Eólica"]
df.shape
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Energía</th>
      <th>Tipo</th>
      <th>Recurso</th>
      <th>Energy</th>
      <th>Nombre del sitio</th>
      <th>Municipio</th>
      <th>Estado</th>
      <th>Permiso</th>
      <th>Latitud</th>
      <th>Longitud</th>
      <th>Inicio de operación</th>
      <th>Productor</th>
      <th>Capacidad instalada (MW)</th>
      <th>Capacidad en operación (MW)</th>
      <th>Unidades de generación</th>
      <th>Producción eléctrica (GWh/año)</th>
      <th>Generación Neta (GWh/año)</th>
      <th>Factor de planta</th>
      <th>URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>99</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Bii Nee Stipa I</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/548/AUT/2006</td>
      <td>16.484234</td>
      <td>-94.994522</td>
      <td>01/04/2010</td>
      <td>Privado</td>
      <td>26.35</td>
      <td>26.35</td>
      <td>31</td>
      <td>91.322000</td>
      <td>90.686000</td>
      <td>0.395631</td>
      <td>documentos/ACTUAL/Eolica/bii_nee_stipa_energia...</td>
    </tr>
    <tr>
      <th>100</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Cuatro</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/851/PIE/2010</td>
      <td>16.612269</td>
      <td>-94.810514</td>
      <td>05/01/2012</td>
      <td>Privado</td>
      <td>102.00</td>
      <td>102.00</td>
      <td>68</td>
      <td>469.064000</td>
      <td>468.324000</td>
      <td>0.524962</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_cuatro.pdf</td>
    </tr>
    <tr>
      <th>101</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Dos</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/850/PIE/2010</td>
      <td>16.587181</td>
      <td>-94.794464</td>
      <td>06/02/2012</td>
      <td>Privado</td>
      <td>102.00</td>
      <td>102.00</td>
      <td>68</td>
      <td>419.568000</td>
      <td>418.680000</td>
      <td>0.469568</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_dos.pdf</td>
    </tr>
    <tr>
      <th>102</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Tres</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/852/PIE/2010</td>
      <td>16.581341</td>
      <td>-94.747944</td>
      <td>30/01/2012</td>
      <td>Privado</td>
      <td>102.00</td>
      <td>102.00</td>
      <td>68</td>
      <td>321.969000</td>
      <td>320.689000</td>
      <td>0.360338</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_tres.pdf</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Guerrero Negro (Puerto Viejo)</td>
      <td>Muleg├®</td>
      <td>Baja California</td>
      <td>E/1570/GEN/2015</td>
      <td>27.976174</td>
      <td>-114.067172</td>
      <td>01/12/1998</td>
      <td>CFE</td>
      <td>0.60</td>
      <td>0.60</td>
      <td>1</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>documentos/ACTUAL/Eolica/central_guerrero_negr...</td>
    </tr>
    <tr>
      <th>104</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>La Venta</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1571/GEN/2015</td>
      <td>16.601750</td>
      <td>-94.834917</td>
      <td>08/07/1994</td>
      <td>CFE</td>
      <td>84.20</td>
      <td>84.20</td>
      <td>104</td>
      <td>184.719031</td>
      <td>183.770502</td>
      <td>0.250435</td>
      <td>documentos/ACTUAL/Eolica/central_la_venta.pdf</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Yuumil Ik</td>
      <td>Benito Juarez</td>
      <td>Quintana Roo</td>
      <td>E/1572/GEN/2015</td>
      <td>20.976080</td>
      <td>-86.862118</td>
      <td>01/06/2011</td>
      <td>CFE</td>
      <td>1.50</td>
      <td>1.50</td>
      <td>1</td>
      <td>2.321977</td>
      <td>2.321977</td>
      <td>0.176711</td>
      <td>documentos/ACTUAL/Eolica/central_yuumulÔÇÖlik.pdf</td>
    </tr>
    <tr>
      <th>106</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Compañía Eólica de Tamaulipas</td>
      <td>Reynosa</td>
      <td>Tamaulipas</td>
      <td>E/863/AUT/2010</td>
      <td>25.970092</td>
      <td>-98.328577</td>
      <td>01/03/2014</td>
      <td>Privado</td>
      <td>54.00</td>
      <td>54.00</td>
      <td>36</td>
      <td>168.830000</td>
      <td>168.830000</td>
      <td>0.356904</td>
      <td>documentos/ACTUAL/Eolica/compa├▒ia_eolica_de_t...</td>
    </tr>
    <tr>
      <th>107</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Parque eólico Piedra Larga Fase 2</td>
      <td>Unión Hidalgo</td>
      <td>Oaxaca</td>
      <td>E/823/AUT/2009</td>
      <td>16.497802</td>
      <td>-94.809892</td>
      <td>01/09/2014</td>
      <td>Privado</td>
      <td>90.00</td>
      <td>90.00</td>
      <td>69</td>
      <td>304.340000</td>
      <td>301.250000</td>
      <td>0.386022</td>
      <td>documentos/ACTUAL/Eolica/desarrollos_eolicos_m...</td>
    </tr>
    <tr>
      <th>108</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólicos Mexicanos de Oaxaca I</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/939/AUT/2012</td>
      <td>16.546048</td>
      <td>-94.828453</td>
      <td>01/11/2012</td>
      <td>Privado</td>
      <td>137.50</td>
      <td>137.50</td>
      <td>152</td>
      <td>491.400000</td>
      <td>486.840000</td>
      <td>0.407970</td>
      <td>documentos/ACTUAL/Eolica/desarrollos_eolicos_m...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Dominica Energía Limpia</td>
      <td>Charcas</td>
      <td>San Luis Potos├¡</td>
      <td>E/894/AUT/2011</td>
      <td>23.329936</td>
      <td>-101.268156</td>
      <td>01/11/2014</td>
      <td>Privado</td>
      <td>200.00</td>
      <td>200.00</td>
      <td>100</td>
      <td>489.466000</td>
      <td>488.986000</td>
      <td>0.279376</td>
      <td>documentos/ACTUAL/Eolica/dominica_energia_limp...</td>
    </tr>
    <tr>
      <th>110</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eléctrica del Valle de México</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/201/AUT/2001</td>
      <td>16.537189</td>
      <td>-94.991577</td>
      <td>01/04/2010</td>
      <td>Privado</td>
      <td>67.50</td>
      <td>67.50</td>
      <td>120</td>
      <td>191.482000</td>
      <td>182.944000</td>
      <td>0.323832</td>
      <td>documentos/ACTUAL/Eolica/electrica_de_valle_de...</td>
    </tr>
    <tr>
      <th>111</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Sierra Juárez</td>
      <td>Tecate</td>
      <td>Baja California</td>
      <td>E/932/EXP/2012</td>
      <td>32.597180</td>
      <td>-116.078700</td>
      <td>30/04/2015</td>
      <td>Privado</td>
      <td>156.00</td>
      <td>156.00</td>
      <td>52</td>
      <td>376.628000</td>
      <td>375.046000</td>
      <td>0.275603</td>
      <td>documentos/ACTUAL/Eolica/energia_sierra_juarez...</td>
    </tr>
    <tr>
      <th>112</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Sonora PPE</td>
      <td>Puerto Pe├▒asco</td>
      <td>Sonora</td>
      <td>E/977/PP/2013</td>
      <td>31.343300</td>
      <td>-113.566783</td>
      <td>01/12/2014</td>
      <td>Privado</td>
      <td>2.00</td>
      <td>2.00</td>
      <td>1</td>
      <td>4.135000</td>
      <td>4.135000</td>
      <td>0.236016</td>
      <td>documentos/ACTUAL/Eolica/energia_sonora_ppe.pdf</td>
    </tr>
    <tr>
      <th>113</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energias Ambientales de Oaxaca</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/828/PIE/2009</td>
      <td>16.564282</td>
      <td>-94.721195</td>
      <td>26/09/2012</td>
      <td>Privado</td>
      <td>102.00</td>
      <td>102.00</td>
      <td>51</td>
      <td>316.800000</td>
      <td>294.760000</td>
      <td>0.354553</td>
      <td>documentos/ACTUAL/Eolica/energias_ambientales_...</td>
    </tr>
    <tr>
      <th>114</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energías Renovables La Mata, S. A. P. I. de C. V.</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/983/PIE/2013</td>
      <td>16.611278</td>
      <td>-95.004556</td>
      <td>28/02/2013</td>
      <td>Privado</td>
      <td>102.00</td>
      <td>102.00</td>
      <td>34</td>
      <td>106.404000</td>
      <td>0.000000</td>
      <td>0.119084</td>
      <td>documentos/ACTUAL/Eolica/energias_renovables_l...</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energías Renovables Venta III</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/829/PIE/2009</td>
      <td>16.584106</td>
      <td>-94.733927</td>
      <td>03/10/2012</td>
      <td>Privado</td>
      <td>102.85</td>
      <td>102.85</td>
      <td>121</td>
      <td>200.930000</td>
      <td>198.840000</td>
      <td>0.223016</td>
      <td>documentos/ACTUAL/Eolica/energias_renovables_v...</td>
    </tr>
    <tr>
      <th>116</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eoliatec del Istmo</td>
      <td>Juchit├ín De Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/322/AUT/2005</td>
      <td>16.440613</td>
      <td>-94.991183</td>
      <td>01/07/2013</td>
      <td>Privado</td>
      <td>164.00</td>
      <td>164.00</td>
      <td>124</td>
      <td>544.751000</td>
      <td>532.573000</td>
      <td>0.379184</td>
      <td>documentos/ACTUAL/Eolica/eoliatec_del_istmo.pdf</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eoliatec del Pacífico</td>
      <td>Santo  Domingo Ingenio</td>
      <td>Oaxaca</td>
      <td>E/685/AUT/2007</td>
      <td>16.528698</td>
      <td>-94.790108</td>
      <td>28/02/2014</td>
      <td>Privado</td>
      <td>160.00</td>
      <td>160.00</td>
      <td>80</td>
      <td>640.252000</td>
      <td>629.114000</td>
      <td>0.456801</td>
      <td>documentos/ACTUAL/Eolica/eoliatec_del_pacifico...</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica de Arriaga</td>
      <td>Arriaga</td>
      <td>Chiapas</td>
      <td>E/920/AUT/2012</td>
      <td>16.184982</td>
      <td>-93.939629</td>
      <td>05/06/2012</td>
      <td>Privado</td>
      <td>32.00</td>
      <td>32.00</td>
      <td>16</td>
      <td>89.605000</td>
      <td>89.090000</td>
      <td>0.319653</td>
      <td>documentos/ACTUAL/Eolica/eolica_de_arriaga.pdf</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Dos Arbolitos, S.A. P. I. de C. V.</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1159/AUT/2014</td>
      <td>16.536994</td>
      <td>-94.961348</td>
      <td>01/12/2014</td>
      <td>Privado</td>
      <td>70.00</td>
      <td>70.00</td>
      <td>35</td>
      <td>225.190000</td>
      <td>223.620000</td>
      <td>0.367237</td>
      <td>documentos/ACTUAL/Eolica/eolica_dos_arbolitos.pdf</td>
    </tr>
    <tr>
      <th>120</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica El Retiro</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1028/AUT/2013</td>
      <td>16.530775</td>
      <td>-94.960956</td>
      <td>01/05/2014</td>
      <td>Privado</td>
      <td>74.00</td>
      <td>74.00</td>
      <td>37</td>
      <td>143.110000</td>
      <td>142.507000</td>
      <td>0.220767</td>
      <td>documentos/ACTUAL/Eolica/eolica_el_retiro.pdf</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Los Altos</td>
      <td>Ojuelos de Jalisco</td>
      <td>Jalisco</td>
      <td>E/979/AUT/2013</td>
      <td>21.853772</td>
      <td>-101.599417</td>
      <td>01/12/2013</td>
      <td>Privado</td>
      <td>64.60</td>
      <td>50.40</td>
      <td>28</td>
      <td>183.231000</td>
      <td>183.022000</td>
      <td>0.415015</td>
      <td>documentos/ACTUAL/Eolica/eolica_los_altos.pdf</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Santa Catarina</td>
      <td>Santa Catarina</td>
      <td>Nuevo Le├│n</td>
      <td>E/802/AUT/2008</td>
      <td>25.683056</td>
      <td>-100.640556</td>
      <td>01/06/2013</td>
      <td>Privado</td>
      <td>22.00</td>
      <td>22.00</td>
      <td>8</td>
      <td>36.835000</td>
      <td>36.835000</td>
      <td>0.191132</td>
      <td>documentos/ACTUAL/Eolica/eolica_santa_catarina...</td>
    </tr>
    <tr>
      <th>123</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Zopiloapan (Bii Nee Stipa III)</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/953/AUT/2012</td>
      <td>16.444821</td>
      <td>-95.058775</td>
      <td>01/01/2013</td>
      <td>Privado</td>
      <td>70.00</td>
      <td>70.00</td>
      <td>35</td>
      <td>261.067000</td>
      <td>260.458000</td>
      <td>0.425745</td>
      <td>documentos/ACTUAL/Eolica/eolica_zopiloapan.pdf</td>
    </tr>
    <tr>
      <th>124</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eurus</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/531/AUT/2006</td>
      <td>16.547534</td>
      <td>-94.830467</td>
      <td>30/06/2009</td>
      <td>Privado</td>
      <td>250.50</td>
      <td>250.50</td>
      <td>300</td>
      <td>963.690000</td>
      <td>962.147000</td>
      <td>0.439163</td>
      <td>documentos/ACTUAL/Eolica/eurus.pdf</td>
    </tr>
    <tr>
      <th>125</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Fuerza Eólica del Istmo</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/70/AUT/98</td>
      <td>16.586349</td>
      <td>-95.001612</td>
      <td>08/10/2011</td>
      <td>Privado</td>
      <td>80.00</td>
      <td>80.00</td>
      <td>60</td>
      <td>189.558000</td>
      <td>186.253000</td>
      <td>0.270488</td>
      <td>documentos/ACTUAL/Eolica/fuerza_eolica_del_ist...</td>
    </tr>
    <tr>
      <th>126</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Fuerza y Energía BII HIOXO</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/806/AUT/2008</td>
      <td>16.411529</td>
      <td>-94.955415</td>
      <td>01/10/2014</td>
      <td>Privado</td>
      <td>234.00</td>
      <td>234.00</td>
      <td>252</td>
      <td>801.777000</td>
      <td>801.777000</td>
      <td>0.391141</td>
      <td>documentos/ACTUAL/Eolica/fuerza_y_energia_BII_...</td>
    </tr>
    <tr>
      <th>127</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Instituto de Investigaciones Eléctricas</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/575/PP/2007</td>
      <td>16.545581</td>
      <td>-94.963352</td>
      <td>01/07/2010</td>
      <td>Privado</td>
      <td>5.00</td>
      <td>0.30</td>
      <td>3</td>
      <td>0.016000</td>
      <td>0.015000</td>
      <td>0.006088</td>
      <td>documentos/ACTUAL/Eolica/instituto_de_investig...</td>
    </tr>
    <tr>
      <th>128</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Municipio de Mexicali</td>
      <td>Mexicali</td>
      <td>Baja California</td>
      <td>E/832/AUT/2009</td>
      <td>32.497764</td>
      <td>-116.089826</td>
      <td>29/10/2009</td>
      <td>Privado</td>
      <td>10.00</td>
      <td>10.00</td>
      <td>5</td>
      <td>24.244284</td>
      <td>22.721089</td>
      <td>0.276761</td>
      <td>documentos/ACTUAL/Eolica/municipio_de_mexicali...</td>
    </tr>
    <tr>
      <th>129</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Parques Ecológicos de México</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/215/AUT/2002</td>
      <td>16.528297</td>
      <td>-94.932617</td>
      <td>31/01/2009</td>
      <td>Privado</td>
      <td>101.90</td>
      <td>101.90</td>
      <td>82</td>
      <td>250.240000</td>
      <td>248.470000</td>
      <td>0.280336</td>
      <td>documentos/ACTUAL/Eolica/parques_ecologicos_de...</td>
    </tr>
    <tr>
      <th>130</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>PE Ingenio, S. de R. de C. V.</td>
      <td>Santo domingo Ingenio</td>
      <td>Oaxaca</td>
      <td>E/1003/AUT/2013</td>
      <td>16.577272</td>
      <td>-94.823510</td>
      <td>27/11/2015</td>
      <td>Privado</td>
      <td>49.50</td>
      <td>49.50</td>
      <td>33</td>
      <td>183.676000</td>
      <td>183.676000</td>
      <td>0.423587</td>
      <td>documentos/ACTUAL/Eolica/pe_ingenio.pdf</td>
    </tr>
    <tr>
      <th>131</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Pier II Quecholac Felipe Ángeles, S. A. de C. V.</td>
      <td>Palmar del Bravo</td>
      <td>Puebla</td>
      <td>E/1054/AUT/2013</td>
      <td>18.815595</td>
      <td>-97.562787</td>
      <td>24/10/2013</td>
      <td>Privado</td>
      <td>66.00</td>
      <td>66.00</td>
      <td>33</td>
      <td>252.580000</td>
      <td>250.820000</td>
      <td>0.436869</td>
      <td>documentos/ACTUAL/Eolica/pier_II_quecholac_fel...</td>
    </tr>
    <tr>
      <th>132</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Stipa Nayaa (Bii Nee Stipa II)</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/907/AUT/2011</td>
      <td>16.496007</td>
      <td>-94.999971</td>
      <td>01/07/2012</td>
      <td>Privado</td>
      <td>74.00</td>
      <td>74.00</td>
      <td>37</td>
      <td>279.425000</td>
      <td>278.833000</td>
      <td>0.431052</td>
      <td>documentos/ACTUAL/Eolica/stipa_nayaa.pdf</td>
    </tr>
    <tr>
      <th>133</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ventika, S. A. de C. V.</td>
      <td>General Bravo</td>
      <td>Nuevo Le├│n</td>
      <td>E/912/AUT/2011</td>
      <td>25.892214</td>
      <td>-98.786667</td>
      <td>01/04/2016</td>
      <td>Privado</td>
      <td>126.00</td>
      <td>126.00</td>
      <td>84</td>
      <td>332.931000</td>
      <td>331.779000</td>
      <td>0.301634</td>
      <td>documentos/ACTUAL/Eolica/ventika.pdf</td>
    </tr>
    <tr>
      <th>134</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ventika 11, S. A. de C. V.</td>
      <td>General Bravo</td>
      <td>Nuevo Le├│n</td>
      <td>E/936/AUT/2012</td>
      <td>25.892214</td>
      <td>-98.786667</td>
      <td>01/04/2016</td>
      <td>Privado</td>
      <td>126.00</td>
      <td>126.00</td>
      <td>47</td>
      <td>356.586000</td>
      <td>355.275000</td>
      <td>0.323065</td>
      <td>documentos/ACTUAL/Eolica/ventika_II.pdf</td>
    </tr>
    <tr>
      <th>135</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Limpia de Palo Alto, S. de R. L. de C. V.</td>
      <td>Ojuelos y Lagos de Moreno</td>
      <td>Aguascalientes</td>
      <td>E/1357/AUT/2015</td>
      <td>21.864167</td>
      <td>-101.593333</td>
      <td>31/12/2016</td>
      <td>Privado</td>
      <td>129.00</td>
      <td>0.00</td>
      <td>0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>documentos/ACTUAL/Eolica/energia_limpia_de_pal...</td>
    </tr>
    <tr>
      <th>136</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica de Coahuila, S.A de C.V</td>
      <td>Ramos Arizpe</td>
      <td>Coahuila</td>
      <td>E/1015/AUT/2013</td>
      <td>25.697523</td>
      <td>-101.403103</td>
      <td>15/12/2016</td>
      <td>Privado</td>
      <td>200.60</td>
      <td>0.00</td>
      <td>118</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>documentos/ACTUAL/Eolica/eolica_de_coahuila.pdf</td>
    </tr>
    <tr>
      <th>137</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Tres Mesas,S de R.L de C.V</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>E/1029/AUT/2013</td>
      <td>23.389212</td>
      <td>-98.990885</td>
      <td>31/12/2016</td>
      <td>Privado</td>
      <td>62.70</td>
      <td>0.00</td>
      <td>19</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>documentos/ACTUAL/Eolica/eolica_tres_mesas.pdf</td>
    </tr>
    <tr>
      <th>138</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>C├¡a Eoloel├®ctrica de Cd. Victoria,S:A de C:V</td>
      <td>G├╝├®mez</td>
      <td>Tamaulipas</td>
      <td>E/945/AUT/2012</td>
      <td>23.789167</td>
      <td>-98.969444</td>
      <td>30/06/2016</td>
      <td>Privado</td>
      <td>50.00</td>
      <td>0.00</td>
      <td>0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>documentos/ACTUAL/Eolica/compa├▒ia_eoloelectri...</td>
    </tr>
    <tr>
      <th>139</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Vientos del Altiplano, S. de R. L. de C. V.</td>
      <td>Mazapil</td>
      <td>Zacatecas</td>
      <td>E/1356/AUT/2015</td>
      <td>23.877375</td>
      <td>-101.736536</td>
      <td>30/06/2016</td>
      <td>Privado</td>
      <td>140.00</td>
      <td>100.00</td>
      <td>0</td>
      <td>39.778000</td>
      <td>39.565000</td>
      <td>0.045409</td>
      <td>documentos/ACTUAL/Eolica/vientos_del_altiplano...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#LEYENDO Y FILTRANDO EXCEL DE CENTRALES EN CONSTRUCCIÓN O POR INICIAR OBRAS
df2 = pd.read_excel("Centrales_potencial.xlsx")
df2 = df2[df2.Energía=="Eólica"]
df2.drop("ID,N,16,6", axis="columns", inplace=True)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Energía</th>
      <th>Tipo</th>
      <th>Recurso</th>
      <th>Energy</th>
      <th>Clasificación</th>
      <th>Subclasificación</th>
      <th>Nombre del sitio</th>
      <th>Municipio</th>
      <th>Estado</th>
      <th>Capacidad instalada (MW)</th>
      <th>Factor de planta</th>
      <th>Potencial de generación (GWh/año)</th>
      <th>Latitud</th>
      <th>Longitud</th>
      <th>Fuente</th>
      <th>Página web</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>En construcci├│n</td>
      <td>AE Mex Global</td>
      <td>General Cepeda</td>
      <td>Coahuila</td>
      <td>96.0</td>
      <td>0.332953</td>
      <td>280.000</td>
      <td>25.792233</td>
      <td>-101.615816</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/ae_mex_global.pdf</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldener ADM,  (Central Parque E├│lico Chacabal...</td>
      <td>Cansahcab</td>
      <td>Yucat├ín</td>
      <td>30.0</td>
      <td>0.457991</td>
      <td>120.360</td>
      <td>21.146367</td>
      <td>-89.131967</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldener_adm_centra...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Cadereyta de Montes</td>
      <td>Quer├®taro</td>
      <td>30.0</td>
      <td>0.304795</td>
      <td>80.100</td>
      <td>20.980783</td>
      <td>-99.700983</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Cardonal</td>
      <td>Hidalgo</td>
      <td>30.0</td>
      <td>0.319578</td>
      <td>83.985</td>
      <td>20.585333</td>
      <td>-99.107400</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Juchique de Ferrer</td>
      <td>Veracruz</td>
      <td>30.0</td>
      <td>0.377968</td>
      <td>99.330</td>
      <td>19.879350</td>
      <td>-96.592850</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>70</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Desarrollo de Fuerzas Renovables (Central Dolo...</td>
      <td>China</td>
      <td>Nuevo Le├│n</td>
      <td>269.0</td>
      <td>0.460440</td>
      <td>1085.000</td>
      <td>25.463786</td>
      <td>-98.578342</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Desarrollo_De_Fuer...</td>
    </tr>
    <tr>
      <th>71</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica Mesa La Paz, S. de R. L. de C. V.</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>300.0</td>
      <td>0.445205</td>
      <td>1170.000</td>
      <td>23.331191</td>
      <td>-98.824562</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Mesa_La_Paz...</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica Tres Mesas 4, S. de R. L. de C. V.</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>95.7</td>
      <td>0.498490</td>
      <td>417.900</td>
      <td>23.399327</td>
      <td>-98.977438</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Tres_Mesas_...</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Desarrollo de Fuerzas Renovables (Central Ener...</td>
      <td>Acu├▒a</td>
      <td>Coahuila</td>
      <td>99.0</td>
      <td>0.456713</td>
      <td>396.080</td>
      <td>29.605983</td>
      <td>-101.701179</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Desarrollo_De_Fuer...</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica del Golfo 4, S. A. de C. V.</td>
      <td>Motul</td>
      <td>Yucat├ín</td>
      <td>88.0</td>
      <td>0.523882</td>
      <td>403.850</td>
      <td>21.278593</td>
      <td>-89.414738</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Del_Golfo_4...</td>
    </tr>
  </tbody>
</table>
<p>75 rows × 16 columns</p>
</div>




```python
df.columns
```




    Index(['Energía', 'Tipo', 'Recurso', 'Energy', 'Nombre del sitio', 'Municipio',
           'Estado', 'Permiso', 'Latitud', 'Longitud', 'Inicio de operación',
           'Productor', 'Capacidad instalada (MW)', 'Capacidad en operación (MW)',
           'Unidades de generación', 'Producción eléctrica (GWh/año)',
           'Generación Neta (GWh/año)', 'Factor de planta', 'URL'],
          dtype='object')




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 41 entries, 99 to 139
    Data columns (total 19 columns):
     #   Column                          Non-Null Count  Dtype  
    ---  ------                          --------------  -----  
     0   Energía                         41 non-null     object 
     1   Tipo                            41 non-null     object 
     2   Recurso                         41 non-null     object 
     3   Energy                          41 non-null     object 
     4   Nombre del sitio                41 non-null     object 
     5   Municipio                       41 non-null     object 
     6   Estado                          41 non-null     object 
     7   Permiso                         41 non-null     object 
     8   Latitud                         41 non-null     float64
     9   Longitud                        41 non-null     float64
     10  Inicio de operación             41 non-null     object 
     11  Productor                       41 non-null     object 
     12  Capacidad instalada (MW)        41 non-null     float64
     13  Capacidad en operación (MW)     41 non-null     float64
     14  Unidades de generación          41 non-null     int64  
     15  Producción eléctrica (GWh/año)  41 non-null     float64
     16  Generación Neta (GWh/año)       41 non-null     float64
     17  Factor de planta                41 non-null     float64
     18  URL                             41 non-null     object 
    dtypes: float64(7), int64(1), object(11)
    memory usage: 6.4+ KB
    


```python
#CONVIRTIENDO A OBJECT LAS VARIABLES NUMÉRICAS DEL DATAFRAME PARA SU MANIPULACIÓN EN EL MAPA

df["Capacidad instalada (MW)"] = df["Capacidad instalada (MW)"].apply(lambda i: str(i))
df["Capacidad en operación (MW)"] = df["Capacidad en operación (MW)"].apply(lambda i: str(i))
df["Producción eléctrica (GWh/año)"] = df["Producción eléctrica (GWh/año)"].apply(lambda i: str(i))
df["Generación Neta (GWh/año)"] = df["Generación Neta (GWh/año)"].apply(lambda i: str(i))
df["Factor de planta"] = df["Factor de planta"].apply(lambda i: str(i))
```


```python
#CONVIRTIENDO A OBJECT LAS VARIABLES NUMÉRICAS DEL DATAFRAME 2 PARA SU MANIPULACIÓN EN EL MAPA

df2["Capacidad instalada (MW)"] = df2["Capacidad instalada (MW)"].apply(lambda i: str(i))
df2["Potencial de generación (GWh/año)"] = df2["Potencial de generación (GWh/año)"].apply(lambda i: str(i))
df2["Factor de planta"] = df2["Factor de planta"].apply(lambda i: str(i))
```


```python
df2["Información"] = df2["Nombre del sitio"] +". Capacidad instalada (MW): " + df2["Capacidad instalada (MW)"]
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Energía</th>
      <th>Tipo</th>
      <th>Recurso</th>
      <th>Energy</th>
      <th>Clasificación</th>
      <th>Subclasificación</th>
      <th>Nombre del sitio</th>
      <th>Municipio</th>
      <th>Estado</th>
      <th>Capacidad instalada (MW)</th>
      <th>Factor de planta</th>
      <th>Potencial de generación (GWh/año)</th>
      <th>Latitud</th>
      <th>Longitud</th>
      <th>Fuente</th>
      <th>Página web</th>
      <th>Información</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>En construcci├│n</td>
      <td>AE Mex Global</td>
      <td>General Cepeda</td>
      <td>Coahuila</td>
      <td>96.0</td>
      <td>0.33295281583</td>
      <td>280.0</td>
      <td>25.792233</td>
      <td>-101.615816</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/ae_mex_global.pdf</td>
      <td>AE Mex Global. Capacidad instalada (MW): 96.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldener ADM,  (Central Parque E├│lico Chacabal...</td>
      <td>Cansahcab</td>
      <td>Yucat├ín</td>
      <td>30.0</td>
      <td>0.45799086757999996</td>
      <td>120.36</td>
      <td>21.146367</td>
      <td>-89.131967</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldener_adm_centra...</td>
      <td>Aldener ADM,  (Central Parque E├│lico Chacabal...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Cadereyta de Montes</td>
      <td>Quer├®taro</td>
      <td>30.0</td>
      <td>0.30479452054800005</td>
      <td>80.1</td>
      <td>20.980783</td>
      <td>-99.700983</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Cardonal</td>
      <td>Hidalgo</td>
      <td>30.0</td>
      <td>0.319577625571</td>
      <td>83.985</td>
      <td>20.585333</td>
      <td>-99.107400</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
      <td>Juchique de Ferrer</td>
      <td>Veracruz</td>
      <td>30.0</td>
      <td>0.37796803653</td>
      <td>99.33</td>
      <td>19.879350</td>
      <td>-96.592850</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/aldesa_energias_re...</td>
      <td>Aldesa Energ├¡as Renovables de M├®xico, Centra...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>70</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Desarrollo de Fuerzas Renovables (Central Dolo...</td>
      <td>China</td>
      <td>Nuevo Le├│n</td>
      <td>269.0</td>
      <td>0.46044032523600004</td>
      <td>1085.0</td>
      <td>25.463786</td>
      <td>-98.578342</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Desarrollo_De_Fuer...</td>
      <td>Desarrollo de Fuerzas Renovables (Central Dolo...</td>
    </tr>
    <tr>
      <th>71</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica Mesa La Paz, S. de R. L. de C. V.</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>300.0</td>
      <td>0.44520547945200006</td>
      <td>1170.0</td>
      <td>23.331191</td>
      <td>-98.824562</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Mesa_La_Paz...</td>
      <td>E├│lica Mesa La Paz, S. de R. L. de C. V.. Cap...</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica Tres Mesas 4, S. de R. L. de C. V.</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>95.7</td>
      <td>0.498489858433</td>
      <td>417.9</td>
      <td>23.399327</td>
      <td>-98.977438</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Tres_Mesas_...</td>
      <td>E├│lica Tres Mesas 4, S. de R. L. de C. V.. Ca...</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>Desarrollo de Fuerzas Renovables (Central Ener...</td>
      <td>Acu├▒a</td>
      <td>Coahuila</td>
      <td>99.0</td>
      <td>0.456713251234</td>
      <td>396.08</td>
      <td>29.605983</td>
      <td>-101.701179</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Desarrollo_De_Fuer...</td>
      <td>Desarrollo de Fuerzas Renovables (Central Ener...</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Eólica</td>
      <td>Aerogenerador convencional</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Probado</td>
      <td>Por iniciar obras</td>
      <td>E├│lica del Golfo 4, S. A. de C. V.</td>
      <td>Motul</td>
      <td>Yucat├ín</td>
      <td>88.0</td>
      <td>0.523881797426</td>
      <td>403.85</td>
      <td>21.278593</td>
      <td>-89.414738</td>
      <td>CRE</td>
      <td>documentos/POTENCIAL/EOLICA/Eolica_Del_Golfo_4...</td>
      <td>E├│lica del Golfo 4, S. A. de C. V.. Capacidad...</td>
    </tr>
  </tbody>
</table>
<p>75 rows × 17 columns</p>
</div>




```python
df["Información"] = df["Nombre del sitio"] +". Capacidad instalada (MW): " + df["Capacidad instalada (MW)"]
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Energía</th>
      <th>Tipo</th>
      <th>Recurso</th>
      <th>Energy</th>
      <th>Nombre del sitio</th>
      <th>Municipio</th>
      <th>Estado</th>
      <th>Permiso</th>
      <th>Latitud</th>
      <th>Longitud</th>
      <th>Inicio de operación</th>
      <th>Productor</th>
      <th>Capacidad instalada (MW)</th>
      <th>Capacidad en operación (MW)</th>
      <th>Unidades de generación</th>
      <th>Producción eléctrica (GWh/año)</th>
      <th>Generación Neta (GWh/año)</th>
      <th>Factor de planta</th>
      <th>URL</th>
      <th>Información</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>99</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Bii Nee Stipa I</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/548/AUT/2006</td>
      <td>16.484234</td>
      <td>-94.994522</td>
      <td>01/04/2010</td>
      <td>Privado</td>
      <td>26.35</td>
      <td>26.35</td>
      <td>31</td>
      <td>91.322</td>
      <td>90.686</td>
      <td>0.39563099999999995</td>
      <td>documentos/ACTUAL/Eolica/bii_nee_stipa_energia...</td>
      <td>Bii Nee Stipa I. Capacidad instalada (MW): 26.35</td>
    </tr>
    <tr>
      <th>100</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Cuatro</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/851/PIE/2010</td>
      <td>16.612269</td>
      <td>-94.810514</td>
      <td>05/01/2012</td>
      <td>Privado</td>
      <td>102.0</td>
      <td>102.0</td>
      <td>68</td>
      <td>469.064</td>
      <td>468.324</td>
      <td>0.5249619999999999</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_cuatro.pdf</td>
      <td>Ce Oaxaca Cuatro. Capacidad instalada (MW): 102.0</td>
    </tr>
    <tr>
      <th>101</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Dos</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/850/PIE/2010</td>
      <td>16.587181</td>
      <td>-94.794464</td>
      <td>06/02/2012</td>
      <td>Privado</td>
      <td>102.0</td>
      <td>102.0</td>
      <td>68</td>
      <td>419.568</td>
      <td>418.68</td>
      <td>0.469568</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_dos.pdf</td>
      <td>Ce Oaxaca Dos. Capacidad instalada (MW): 102.0</td>
    </tr>
    <tr>
      <th>102</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ce Oaxaca Tres</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/852/PIE/2010</td>
      <td>16.581341</td>
      <td>-94.747944</td>
      <td>30/01/2012</td>
      <td>Privado</td>
      <td>102.0</td>
      <td>102.0</td>
      <td>68</td>
      <td>321.969</td>
      <td>320.689</td>
      <td>0.360338</td>
      <td>documentos/ACTUAL/Eolica/ce_oaxaca_tres.pdf</td>
      <td>Ce Oaxaca Tres. Capacidad instalada (MW): 102.0</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Guerrero Negro (Puerto Viejo)</td>
      <td>Muleg├®</td>
      <td>Baja California</td>
      <td>E/1570/GEN/2015</td>
      <td>27.976174</td>
      <td>-114.067172</td>
      <td>01/12/1998</td>
      <td>CFE</td>
      <td>0.6</td>
      <td>0.6</td>
      <td>1</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>documentos/ACTUAL/Eolica/central_guerrero_negr...</td>
      <td>Guerrero Negro (Puerto Viejo). Capacidad insta...</td>
    </tr>
    <tr>
      <th>104</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>La Venta</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1571/GEN/2015</td>
      <td>16.601750</td>
      <td>-94.834917</td>
      <td>08/07/1994</td>
      <td>CFE</td>
      <td>84.2</td>
      <td>84.2</td>
      <td>104</td>
      <td>184.719031</td>
      <td>183.770502</td>
      <td>0.25043499999999996</td>
      <td>documentos/ACTUAL/Eolica/central_la_venta.pdf</td>
      <td>La Venta. Capacidad instalada (MW): 84.2</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Yuumil Ik</td>
      <td>Benito Juarez</td>
      <td>Quintana Roo</td>
      <td>E/1572/GEN/2015</td>
      <td>20.976080</td>
      <td>-86.862118</td>
      <td>01/06/2011</td>
      <td>CFE</td>
      <td>1.5</td>
      <td>1.5</td>
      <td>1</td>
      <td>2.321977</td>
      <td>2.321977</td>
      <td>0.17671099999999998</td>
      <td>documentos/ACTUAL/Eolica/central_yuumulÔÇÖlik.pdf</td>
      <td>Yuumil Ik. Capacidad instalada (MW): 1.5</td>
    </tr>
    <tr>
      <th>106</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Compañía Eólica de Tamaulipas</td>
      <td>Reynosa</td>
      <td>Tamaulipas</td>
      <td>E/863/AUT/2010</td>
      <td>25.970092</td>
      <td>-98.328577</td>
      <td>01/03/2014</td>
      <td>Privado</td>
      <td>54.0</td>
      <td>54.0</td>
      <td>36</td>
      <td>168.83</td>
      <td>168.83</td>
      <td>0.356904</td>
      <td>documentos/ACTUAL/Eolica/compa├▒ia_eolica_de_t...</td>
      <td>Compañía Eólica de Tamaulipas. Capacidad insta...</td>
    </tr>
    <tr>
      <th>107</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Parque eólico Piedra Larga Fase 2</td>
      <td>Unión Hidalgo</td>
      <td>Oaxaca</td>
      <td>E/823/AUT/2009</td>
      <td>16.497802</td>
      <td>-94.809892</td>
      <td>01/09/2014</td>
      <td>Privado</td>
      <td>90.0</td>
      <td>90.0</td>
      <td>69</td>
      <td>304.34</td>
      <td>301.25</td>
      <td>0.386022</td>
      <td>documentos/ACTUAL/Eolica/desarrollos_eolicos_m...</td>
      <td>Parque eólico Piedra Larga Fase 2. Capacidad i...</td>
    </tr>
    <tr>
      <th>108</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólicos Mexicanos de Oaxaca I</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/939/AUT/2012</td>
      <td>16.546048</td>
      <td>-94.828453</td>
      <td>01/11/2012</td>
      <td>Privado</td>
      <td>137.5</td>
      <td>137.5</td>
      <td>152</td>
      <td>491.4</td>
      <td>486.84</td>
      <td>0.40797</td>
      <td>documentos/ACTUAL/Eolica/desarrollos_eolicos_m...</td>
      <td>Eólicos Mexicanos de Oaxaca I. Capacidad insta...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Dominica Energía Limpia</td>
      <td>Charcas</td>
      <td>San Luis Potos├¡</td>
      <td>E/894/AUT/2011</td>
      <td>23.329936</td>
      <td>-101.268156</td>
      <td>01/11/2014</td>
      <td>Privado</td>
      <td>200.0</td>
      <td>200.0</td>
      <td>100</td>
      <td>489.466</td>
      <td>488.986</td>
      <td>0.279376</td>
      <td>documentos/ACTUAL/Eolica/dominica_energia_limp...</td>
      <td>Dominica Energía Limpia. Capacidad instalada (...</td>
    </tr>
    <tr>
      <th>110</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eléctrica del Valle de México</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/201/AUT/2001</td>
      <td>16.537189</td>
      <td>-94.991577</td>
      <td>01/04/2010</td>
      <td>Privado</td>
      <td>67.5</td>
      <td>67.5</td>
      <td>120</td>
      <td>191.482</td>
      <td>182.944</td>
      <td>0.323832</td>
      <td>documentos/ACTUAL/Eolica/electrica_de_valle_de...</td>
      <td>Eléctrica del Valle de México. Capacidad insta...</td>
    </tr>
    <tr>
      <th>111</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Sierra Juárez</td>
      <td>Tecate</td>
      <td>Baja California</td>
      <td>E/932/EXP/2012</td>
      <td>32.597180</td>
      <td>-116.078700</td>
      <td>30/04/2015</td>
      <td>Privado</td>
      <td>156.0</td>
      <td>156.0</td>
      <td>52</td>
      <td>376.628</td>
      <td>375.046</td>
      <td>0.275603</td>
      <td>documentos/ACTUAL/Eolica/energia_sierra_juarez...</td>
      <td>Energía Sierra Juárez. Capacidad instalada (MW...</td>
    </tr>
    <tr>
      <th>112</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Sonora PPE</td>
      <td>Puerto Pe├▒asco</td>
      <td>Sonora</td>
      <td>E/977/PP/2013</td>
      <td>31.343300</td>
      <td>-113.566783</td>
      <td>01/12/2014</td>
      <td>Privado</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1</td>
      <td>4.135</td>
      <td>4.135</td>
      <td>0.23601599999999998</td>
      <td>documentos/ACTUAL/Eolica/energia_sonora_ppe.pdf</td>
      <td>Energía Sonora PPE. Capacidad instalada (MW): 2.0</td>
    </tr>
    <tr>
      <th>113</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energias Ambientales de Oaxaca</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/828/PIE/2009</td>
      <td>16.564282</td>
      <td>-94.721195</td>
      <td>26/09/2012</td>
      <td>Privado</td>
      <td>102.0</td>
      <td>102.0</td>
      <td>51</td>
      <td>316.8</td>
      <td>294.76</td>
      <td>0.354553</td>
      <td>documentos/ACTUAL/Eolica/energias_ambientales_...</td>
      <td>Energias Ambientales de Oaxaca. Capacidad inst...</td>
    </tr>
    <tr>
      <th>114</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energías Renovables La Mata, S. A. P. I. de C. V.</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/983/PIE/2013</td>
      <td>16.611278</td>
      <td>-95.004556</td>
      <td>28/02/2013</td>
      <td>Privado</td>
      <td>102.0</td>
      <td>102.0</td>
      <td>34</td>
      <td>106.404</td>
      <td>0.0</td>
      <td>0.119084</td>
      <td>documentos/ACTUAL/Eolica/energias_renovables_l...</td>
      <td>Energías Renovables La Mata, S. A. P. I. de C....</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energías Renovables Venta III</td>
      <td>Santo  Domingo</td>
      <td>Oaxaca</td>
      <td>E/829/PIE/2009</td>
      <td>16.584106</td>
      <td>-94.733927</td>
      <td>03/10/2012</td>
      <td>Privado</td>
      <td>102.85</td>
      <td>102.85</td>
      <td>121</td>
      <td>200.93</td>
      <td>198.84</td>
      <td>0.223016</td>
      <td>documentos/ACTUAL/Eolica/energias_renovables_v...</td>
      <td>Energías Renovables Venta III. Capacidad insta...</td>
    </tr>
    <tr>
      <th>116</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eoliatec del Istmo</td>
      <td>Juchit├ín De Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/322/AUT/2005</td>
      <td>16.440613</td>
      <td>-94.991183</td>
      <td>01/07/2013</td>
      <td>Privado</td>
      <td>164.0</td>
      <td>164.0</td>
      <td>124</td>
      <td>544.751</td>
      <td>532.573</td>
      <td>0.37918399999999997</td>
      <td>documentos/ACTUAL/Eolica/eoliatec_del_istmo.pdf</td>
      <td>Eoliatec del Istmo. Capacidad instalada (MW): ...</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eoliatec del Pacífico</td>
      <td>Santo  Domingo Ingenio</td>
      <td>Oaxaca</td>
      <td>E/685/AUT/2007</td>
      <td>16.528698</td>
      <td>-94.790108</td>
      <td>28/02/2014</td>
      <td>Privado</td>
      <td>160.0</td>
      <td>160.0</td>
      <td>80</td>
      <td>640.252</td>
      <td>629.114</td>
      <td>0.45680099999999996</td>
      <td>documentos/ACTUAL/Eolica/eoliatec_del_pacifico...</td>
      <td>Eoliatec del Pacífico. Capacidad instalada (MW...</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica de Arriaga</td>
      <td>Arriaga</td>
      <td>Chiapas</td>
      <td>E/920/AUT/2012</td>
      <td>16.184982</td>
      <td>-93.939629</td>
      <td>05/06/2012</td>
      <td>Privado</td>
      <td>32.0</td>
      <td>32.0</td>
      <td>16</td>
      <td>89.605</td>
      <td>89.09</td>
      <td>0.31965299999999996</td>
      <td>documentos/ACTUAL/Eolica/eolica_de_arriaga.pdf</td>
      <td>Eólica de Arriaga. Capacidad instalada (MW): 32.0</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Dos Arbolitos, S.A. P. I. de C. V.</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1159/AUT/2014</td>
      <td>16.536994</td>
      <td>-94.961348</td>
      <td>01/12/2014</td>
      <td>Privado</td>
      <td>70.0</td>
      <td>70.0</td>
      <td>35</td>
      <td>225.19</td>
      <td>223.62</td>
      <td>0.367237</td>
      <td>documentos/ACTUAL/Eolica/eolica_dos_arbolitos.pdf</td>
      <td>Eólica Dos Arbolitos, S.A. P. I. de C. V.. Cap...</td>
    </tr>
    <tr>
      <th>120</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica El Retiro</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/1028/AUT/2013</td>
      <td>16.530775</td>
      <td>-94.960956</td>
      <td>01/05/2014</td>
      <td>Privado</td>
      <td>74.0</td>
      <td>74.0</td>
      <td>37</td>
      <td>143.11</td>
      <td>142.507</td>
      <td>0.220767</td>
      <td>documentos/ACTUAL/Eolica/eolica_el_retiro.pdf</td>
      <td>Eólica El Retiro. Capacidad instalada (MW): 74.0</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Los Altos</td>
      <td>Ojuelos de Jalisco</td>
      <td>Jalisco</td>
      <td>E/979/AUT/2013</td>
      <td>21.853772</td>
      <td>-101.599417</td>
      <td>01/12/2013</td>
      <td>Privado</td>
      <td>64.6</td>
      <td>50.4</td>
      <td>28</td>
      <td>183.231</td>
      <td>183.022</td>
      <td>0.41501499999999997</td>
      <td>documentos/ACTUAL/Eolica/eolica_los_altos.pdf</td>
      <td>Los Altos. Capacidad instalada (MW): 64.6</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Santa Catarina</td>
      <td>Santa Catarina</td>
      <td>Nuevo Le├│n</td>
      <td>E/802/AUT/2008</td>
      <td>25.683056</td>
      <td>-100.640556</td>
      <td>01/06/2013</td>
      <td>Privado</td>
      <td>22.0</td>
      <td>22.0</td>
      <td>8</td>
      <td>36.835</td>
      <td>36.835</td>
      <td>0.191132</td>
      <td>documentos/ACTUAL/Eolica/eolica_santa_catarina...</td>
      <td>Eólica Santa Catarina. Capacidad instalada (MW...</td>
    </tr>
    <tr>
      <th>123</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Zopiloapan (Bii Nee Stipa III)</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/953/AUT/2012</td>
      <td>16.444821</td>
      <td>-95.058775</td>
      <td>01/01/2013</td>
      <td>Privado</td>
      <td>70.0</td>
      <td>70.0</td>
      <td>35</td>
      <td>261.067</td>
      <td>260.458</td>
      <td>0.425745</td>
      <td>documentos/ACTUAL/Eolica/eolica_zopiloapan.pdf</td>
      <td>Eólica Zopiloapan (Bii Nee Stipa III). Capacid...</td>
    </tr>
    <tr>
      <th>124</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eurus</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/531/AUT/2006</td>
      <td>16.547534</td>
      <td>-94.830467</td>
      <td>30/06/2009</td>
      <td>Privado</td>
      <td>250.5</td>
      <td>250.5</td>
      <td>300</td>
      <td>963.69</td>
      <td>962.147</td>
      <td>0.43916299999999997</td>
      <td>documentos/ACTUAL/Eolica/eurus.pdf</td>
      <td>Eurus. Capacidad instalada (MW): 250.5</td>
    </tr>
    <tr>
      <th>125</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Fuerza Eólica del Istmo</td>
      <td>Ixtaltepec</td>
      <td>Oaxaca</td>
      <td>E/70/AUT/98</td>
      <td>16.586349</td>
      <td>-95.001612</td>
      <td>08/10/2011</td>
      <td>Privado</td>
      <td>80.0</td>
      <td>80.0</td>
      <td>60</td>
      <td>189.558</td>
      <td>186.253</td>
      <td>0.270488</td>
      <td>documentos/ACTUAL/Eolica/fuerza_eolica_del_ist...</td>
      <td>Fuerza Eólica del Istmo. Capacidad instalada (...</td>
    </tr>
    <tr>
      <th>126</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Fuerza y Energía BII HIOXO</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/806/AUT/2008</td>
      <td>16.411529</td>
      <td>-94.955415</td>
      <td>01/10/2014</td>
      <td>Privado</td>
      <td>234.0</td>
      <td>234.0</td>
      <td>252</td>
      <td>801.777</td>
      <td>801.777</td>
      <td>0.39114099999999996</td>
      <td>documentos/ACTUAL/Eolica/fuerza_y_energia_BII_...</td>
      <td>Fuerza y Energía BII HIOXO. Capacidad instalad...</td>
    </tr>
    <tr>
      <th>127</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Instituto de Investigaciones Eléctricas</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/575/PP/2007</td>
      <td>16.545581</td>
      <td>-94.963352</td>
      <td>01/07/2010</td>
      <td>Privado</td>
      <td>5.0</td>
      <td>0.3</td>
      <td>3</td>
      <td>0.016</td>
      <td>0.015</td>
      <td>0.006088</td>
      <td>documentos/ACTUAL/Eolica/instituto_de_investig...</td>
      <td>Instituto de Investigaciones Eléctricas. Capac...</td>
    </tr>
    <tr>
      <th>128</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Municipio de Mexicali</td>
      <td>Mexicali</td>
      <td>Baja California</td>
      <td>E/832/AUT/2009</td>
      <td>32.497764</td>
      <td>-116.089826</td>
      <td>29/10/2009</td>
      <td>Privado</td>
      <td>10.0</td>
      <td>10.0</td>
      <td>5</td>
      <td>24.244284</td>
      <td>22.721089</td>
      <td>0.276761</td>
      <td>documentos/ACTUAL/Eolica/municipio_de_mexicali...</td>
      <td>Municipio de Mexicali. Capacidad instalada (MW...</td>
    </tr>
    <tr>
      <th>129</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Parques Ecológicos de México</td>
      <td>Juchit├ín de Zaragoza</td>
      <td>Oaxaca</td>
      <td>E/215/AUT/2002</td>
      <td>16.528297</td>
      <td>-94.932617</td>
      <td>31/01/2009</td>
      <td>Privado</td>
      <td>101.9</td>
      <td>101.9</td>
      <td>82</td>
      <td>250.24</td>
      <td>248.47</td>
      <td>0.280336</td>
      <td>documentos/ACTUAL/Eolica/parques_ecologicos_de...</td>
      <td>Parques Ecológicos de México. Capacidad instal...</td>
    </tr>
    <tr>
      <th>130</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>PE Ingenio, S. de R. de C. V.</td>
      <td>Santo domingo Ingenio</td>
      <td>Oaxaca</td>
      <td>E/1003/AUT/2013</td>
      <td>16.577272</td>
      <td>-94.823510</td>
      <td>27/11/2015</td>
      <td>Privado</td>
      <td>49.5</td>
      <td>49.5</td>
      <td>33</td>
      <td>183.676</td>
      <td>183.676</td>
      <td>0.423587</td>
      <td>documentos/ACTUAL/Eolica/pe_ingenio.pdf</td>
      <td>PE Ingenio, S. de R. de C. V.. Capacidad insta...</td>
    </tr>
    <tr>
      <th>131</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Pier II Quecholac Felipe Ángeles, S. A. de C. V.</td>
      <td>Palmar del Bravo</td>
      <td>Puebla</td>
      <td>E/1054/AUT/2013</td>
      <td>18.815595</td>
      <td>-97.562787</td>
      <td>24/10/2013</td>
      <td>Privado</td>
      <td>66.0</td>
      <td>66.0</td>
      <td>33</td>
      <td>252.58</td>
      <td>250.82</td>
      <td>0.436869</td>
      <td>documentos/ACTUAL/Eolica/pier_II_quecholac_fel...</td>
      <td>Pier II Quecholac Felipe Ángeles, S. A. de C. ...</td>
    </tr>
    <tr>
      <th>132</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Stipa Nayaa (Bii Nee Stipa II)</td>
      <td>El Espinal</td>
      <td>Oaxaca</td>
      <td>E/907/AUT/2011</td>
      <td>16.496007</td>
      <td>-94.999971</td>
      <td>01/07/2012</td>
      <td>Privado</td>
      <td>74.0</td>
      <td>74.0</td>
      <td>37</td>
      <td>279.425</td>
      <td>278.833</td>
      <td>0.431052</td>
      <td>documentos/ACTUAL/Eolica/stipa_nayaa.pdf</td>
      <td>Stipa Nayaa (Bii Nee Stipa II). Capacidad inst...</td>
    </tr>
    <tr>
      <th>133</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ventika, S. A. de C. V.</td>
      <td>General Bravo</td>
      <td>Nuevo Le├│n</td>
      <td>E/912/AUT/2011</td>
      <td>25.892214</td>
      <td>-98.786667</td>
      <td>01/04/2016</td>
      <td>Privado</td>
      <td>126.0</td>
      <td>126.0</td>
      <td>84</td>
      <td>332.931</td>
      <td>331.779</td>
      <td>0.301634</td>
      <td>documentos/ACTUAL/Eolica/ventika.pdf</td>
      <td>Ventika, S. A. de C. V.. Capacidad instalada (...</td>
    </tr>
    <tr>
      <th>134</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Ventika 11, S. A. de C. V.</td>
      <td>General Bravo</td>
      <td>Nuevo Le├│n</td>
      <td>E/936/AUT/2012</td>
      <td>25.892214</td>
      <td>-98.786667</td>
      <td>01/04/2016</td>
      <td>Privado</td>
      <td>126.0</td>
      <td>126.0</td>
      <td>47</td>
      <td>356.586</td>
      <td>355.275</td>
      <td>0.323065</td>
      <td>documentos/ACTUAL/Eolica/ventika_II.pdf</td>
      <td>Ventika 11, S. A. de C. V.. Capacidad instalad...</td>
    </tr>
    <tr>
      <th>135</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Energía Limpia de Palo Alto, S. de R. L. de C. V.</td>
      <td>Ojuelos y Lagos de Moreno</td>
      <td>Aguascalientes</td>
      <td>E/1357/AUT/2015</td>
      <td>21.864167</td>
      <td>-101.593333</td>
      <td>31/12/2016</td>
      <td>Privado</td>
      <td>129.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>documentos/ACTUAL/Eolica/energia_limpia_de_pal...</td>
      <td>Energía Limpia de Palo Alto, S. de R. L. de C....</td>
    </tr>
    <tr>
      <th>136</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica de Coahuila, S.A de C.V</td>
      <td>Ramos Arizpe</td>
      <td>Coahuila</td>
      <td>E/1015/AUT/2013</td>
      <td>25.697523</td>
      <td>-101.403103</td>
      <td>15/12/2016</td>
      <td>Privado</td>
      <td>200.6</td>
      <td>0.0</td>
      <td>118</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>documentos/ACTUAL/Eolica/eolica_de_coahuila.pdf</td>
      <td>Eólica de Coahuila, S.A de C.V. Capacidad inst...</td>
    </tr>
    <tr>
      <th>137</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Eólica Tres Mesas,S de R.L de C.V</td>
      <td>Llera</td>
      <td>Tamaulipas</td>
      <td>E/1029/AUT/2013</td>
      <td>23.389212</td>
      <td>-98.990885</td>
      <td>31/12/2016</td>
      <td>Privado</td>
      <td>62.7</td>
      <td>0.0</td>
      <td>19</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>documentos/ACTUAL/Eolica/eolica_tres_mesas.pdf</td>
      <td>Eólica Tres Mesas,S de R.L de C.V. Capacidad i...</td>
    </tr>
    <tr>
      <th>138</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>C├¡a Eoloel├®ctrica de Cd. Victoria,S:A de C:V</td>
      <td>G├╝├®mez</td>
      <td>Tamaulipas</td>
      <td>E/945/AUT/2012</td>
      <td>23.789167</td>
      <td>-98.969444</td>
      <td>30/06/2016</td>
      <td>Privado</td>
      <td>50.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>documentos/ACTUAL/Eolica/compa├▒ia_eoloelectri...</td>
      <td>C├¡a Eoloel├®ctrica de Cd. Victoria,S:A de C:V...</td>
    </tr>
    <tr>
      <th>139</th>
      <td>Eólica</td>
      <td>Aerogenerador</td>
      <td>Viento</td>
      <td>Wind</td>
      <td>Vientos del Altiplano, S. de R. L. de C. V.</td>
      <td>Mazapil</td>
      <td>Zacatecas</td>
      <td>E/1356/AUT/2015</td>
      <td>23.877375</td>
      <td>-101.736536</td>
      <td>30/06/2016</td>
      <td>Privado</td>
      <td>140.0</td>
      <td>100.0</td>
      <td>0</td>
      <td>39.778</td>
      <td>39.565</td>
      <td>0.045409</td>
      <td>documentos/ACTUAL/Eolica/vientos_del_altiplano...</td>
      <td>Vientos del Altiplano, S. de R. L. de C. V.. C...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#CREANDO LAS LISTAS A USAR EN EL MAPA
centrales_en_operacion = df["Información"].tolist()
latitud_operacion = df.Latitud.tolist()
longitud_operacion = df.Longitud.tolist()
```


```python
#CREANDO LAS LISTAS A USAR EN EL MAPA
centrales_potencial = df2["Información"].tolist()
latitud_potencial = df2.Latitud.tolist()
longitud_potencial = df2.Longitud.tolist()
```


```python
!pip install plotly 
!pip install cufflinks
```

    Requirement already satisfied: plotly in c:\users\mpbailon\anaconda\lib\site-packages (4.9.0)
    Requirement already satisfied: six in c:\users\mpbailon\anaconda\lib\site-packages (from plotly) (1.16.0)
    Requirement already satisfied: retrying>=1.3.3 in c:\users\mpbailon\anaconda\lib\site-packages (from plotly) (1.3.3)
    Requirement already satisfied: cufflinks in c:\users\mpbailon\anaconda\lib\site-packages (0.17.3)
    Requirement already satisfied: ipywidgets>=7.0.0 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (7.6.3)
    Requirement already satisfied: pandas>=0.19.2 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (1.2.4)
    Requirement already satisfied: ipython>=5.3.0 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (7.22.0)
    Requirement already satisfied: six>=1.9.0 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (1.16.0)
    Requirement already satisfied: setuptools>=34.4.1 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (52.0.0.post20210125)
    Requirement already satisfied: colorlover>=0.2.1 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (0.3.0)
    Requirement already satisfied: numpy>=1.9.2 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (1.20.2)
    Requirement already satisfied: plotly>=4.1.1 in c:\users\mpbailon\anaconda\lib\site-packages (from cufflinks) (4.9.0)
    Requirement already satisfied: pygments in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (2.9.0)
    Requirement already satisfied: colorama in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (0.4.4)
    Requirement already satisfied: backcall in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (0.2.0)
    Requirement already satisfied: traitlets>=4.2 in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (5.0.5)
    Requirement already satisfied: jedi>=0.16 in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (0.18.0)
    Requirement already satisfied: decorator in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (4.4.2)
    Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (3.0.17)
    Requirement already satisfied: pickleshare in c:\users\mpbailon\anaconda\lib\site-packages (from ipython>=5.3.0->cufflinks) (0.7.5)
    Requirement already satisfied: jupyterlab-widgets>=1.0.0 in c:\users\mpbailon\anaconda\lib\site-packages (from ipywidgets>=7.0.0->cufflinks) (1.0.0)
    Requirement already satisfied: ipykernel>=4.5.1 in c:\users\mpbailon\anaconda\lib\site-packages (from ipywidgets>=7.0.0->cufflinks) (5.3.4)
    Requirement already satisfied: nbformat>=4.2.0 in c:\users\mpbailon\anaconda\lib\site-packages (from ipywidgets>=7.0.0->cufflinks) (5.1.3)
    Requirement already satisfied: widgetsnbextension~=3.5.0 in c:\users\mpbailon\anaconda\lib\site-packages (from ipywidgets>=7.0.0->cufflinks) (3.5.1)
    Requirement already satisfied: jupyter-client in c:\users\mpbailon\anaconda\lib\site-packages (from ipykernel>=4.5.1->ipywidgets>=7.0.0->cufflinks) (6.1.12)
    Requirement already satisfied: tornado>=4.2 in c:\users\mpbailon\anaconda\lib\site-packages (from ipykernel>=4.5.1->ipywidgets>=7.0.0->cufflinks) (6.1)
    Requirement already satisfied: parso<0.9.0,>=0.8.0 in c:\users\mpbailon\anaconda\lib\site-packages (from jedi>=0.16->ipython>=5.3.0->cufflinks) (0.8.2)
    Requirement already satisfied: ipython-genutils in c:\users\mpbailon\anaconda\lib\site-packages (from nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (0.2.0)
    Requirement already satisfied: jupyter-core in c:\users\mpbailon\anaconda\lib\site-packages (from nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (4.7.1)
    Requirement already satisfied: jsonschema!=2.5.0,>=2.4 in c:\users\mpbailon\anaconda\lib\site-packages (from nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (3.2.0)
    Requirement already satisfied: importlib-metadata in c:\users\mpbailon\anaconda\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (3.10.0)
    Requirement already satisfied: attrs>=17.4.0 in c:\users\mpbailon\anaconda\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (21.2.0)
    Requirement already satisfied: pyrsistent>=0.14.0 in c:\users\mpbailon\anaconda\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (0.17.3)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\users\mpbailon\anaconda\lib\site-packages (from pandas>=0.19.2->cufflinks) (2.8.1)
    Requirement already satisfied: pytz>=2017.3 in c:\users\mpbailon\anaconda\lib\site-packages (from pandas>=0.19.2->cufflinks) (2021.1)
    Requirement already satisfied: retrying>=1.3.3 in c:\users\mpbailon\anaconda\lib\site-packages (from plotly>=4.1.1->cufflinks) (1.3.3)
    Requirement already satisfied: wcwidth in c:\users\mpbailon\anaconda\lib\site-packages (from prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0->ipython>=5.3.0->cufflinks) (0.2.5)
    Requirement already satisfied: notebook>=4.4.1 in c:\users\mpbailon\anaconda\lib\site-packages (from widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (6.4.0)
    Requirement already satisfied: Send2Trash>=1.5.0 in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (1.5.0)
    Requirement already satisfied: jinja2 in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (3.0.0)
    Requirement already satisfied: terminado>=0.8.3 in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.9.4)
    Requirement already satisfied: prometheus-client in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.11.0)
    Requirement already satisfied: argon2-cffi in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (20.1.0)
    Requirement already satisfied: nbconvert in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (6.0.7)
    Requirement already satisfied: pyzmq>=17 in c:\users\mpbailon\anaconda\lib\site-packages (from notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (20.0.0)
    Requirement already satisfied: pywin32>=1.0 in c:\users\mpbailon\anaconda\lib\site-packages (from jupyter-core->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (227)
    Requirement already satisfied: pywinpty>=0.5 in c:\users\mpbailon\anaconda\lib\site-packages (from terminado>=0.8.3->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.5.7)
    Requirement already satisfied: cffi>=1.0.0 in c:\users\mpbailon\anaconda\lib\site-packages (from argon2-cffi->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (1.14.5)
    Requirement already satisfied: pycparser in c:\users\mpbailon\anaconda\lib\site-packages (from cffi>=1.0.0->argon2-cffi->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (2.20)
    Requirement already satisfied: zipp>=0.5 in c:\users\mpbailon\anaconda\lib\site-packages (from importlib-metadata->jsonschema!=2.5.0,>=2.4->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (3.4.1)
    Requirement already satisfied: typing-extensions>=3.6.4 in c:\users\mpbailon\anaconda\lib\site-packages (from importlib-metadata->jsonschema!=2.5.0,>=2.4->nbformat>=4.2.0->ipywidgets>=7.0.0->cufflinks) (3.7.4.3)
    Requirement already satisfied: MarkupSafe>=2.0.0rc2 in c:\users\mpbailon\anaconda\lib\site-packages (from jinja2->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (2.0.1)
    Requirement already satisfied: testpath in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.4.4)
    Requirement already satisfied: pandocfilters>=1.4.1 in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (1.4.3)
    Requirement already satisfied: jupyterlab-pygments in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.1.2)
    Requirement already satisfied: defusedxml in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.7.1)
    Requirement already satisfied: entrypoints>=0.2.2 in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.3)
    Requirement already satisfied: bleach in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (3.3.0)
    Requirement already satisfied: nbclient<0.6.0,>=0.5.0 in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.5.3)
    Requirement already satisfied: mistune<2,>=0.8.1 in c:\users\mpbailon\anaconda\lib\site-packages (from nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.8.4)
    Requirement already satisfied: async-generator in c:\users\mpbailon\anaconda\lib\site-packages (from nbclient<0.6.0,>=0.5.0->nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (1.10)
    Requirement already satisfied: nest-asyncio in c:\users\mpbailon\anaconda\lib\site-packages (from nbclient<0.6.0,>=0.5.0->nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (1.5.1)
    Requirement already satisfied: packaging in c:\users\mpbailon\anaconda\lib\site-packages (from bleach->nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (20.9)
    Requirement already satisfied: webencodings in c:\users\mpbailon\anaconda\lib\site-packages (from bleach->nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (0.5.1)
    Requirement already satisfied: pyparsing>=2.0.2 in c:\users\mpbailon\anaconda\lib\site-packages (from packaging->bleach->nbconvert->notebook>=4.4.1->widgetsnbextension~=3.5.0->ipywidgets>=7.0.0->cufflinks) (2.4.7)
    


```python
!pip install mapboxgl_notebook
```

    Requirement already satisfied: mapboxgl_notebook in c:\users\mpbailon\anaconda\lib\site-packages (0.7)
    Requirement already satisfied: jinja2 in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl_notebook) (3.0.0)
    Requirement already satisfied: mapboxgl in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl_notebook) (0.10.2)
    Requirement already satisfied: IPython in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl_notebook) (7.22.0)
    Requirement already satisfied: nssjson in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl_notebook) (0.7)
    Requirement already satisfied: pickleshare in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (0.7.5)
    Requirement already satisfied: backcall in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (0.2.0)
    Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (3.0.17)
    Requirement already satisfied: pygments in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (2.9.0)
    Requirement already satisfied: decorator in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (4.4.2)
    Requirement already satisfied: jedi>=0.16 in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (0.18.0)
    Requirement already satisfied: setuptools>=18.5 in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (52.0.0.post20210125)
    Requirement already satisfied: colorama in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (0.4.4)
    Requirement already satisfied: traitlets>=4.2 in c:\users\mpbailon\anaconda\lib\site-packages (from IPython->mapboxgl_notebook) (5.0.5)
    Requirement already satisfied: parso<0.9.0,>=0.8.0 in c:\users\mpbailon\anaconda\lib\site-packages (from jedi>=0.16->IPython->mapboxgl_notebook) (0.8.2)
    Requirement already satisfied: wcwidth in c:\users\mpbailon\anaconda\lib\site-packages (from prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0->IPython->mapboxgl_notebook) (0.2.5)
    Requirement already satisfied: ipython-genutils in c:\users\mpbailon\anaconda\lib\site-packages (from traitlets>=4.2->IPython->mapboxgl_notebook) (0.2.0)
    Requirement already satisfied: MarkupSafe>=2.0.0rc2 in c:\users\mpbailon\anaconda\lib\site-packages (from jinja2->mapboxgl_notebook) (2.0.1)
    Requirement already satisfied: colour in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl->mapboxgl_notebook) (0.1.5)
    Requirement already satisfied: geojson in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl->mapboxgl_notebook) (2.5.0)
    Requirement already satisfied: matplotlib in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl->mapboxgl_notebook) (3.3.4)
    Requirement already satisfied: chroma-py in c:\users\mpbailon\anaconda\lib\site-packages (from mapboxgl->mapboxgl_notebook) (0.1.0.dev1)
    Requirement already satisfied: cycler>=0.10 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (0.10.0)
    Requirement already satisfied: python-dateutil>=2.1 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (2.8.1)
    Requirement already satisfied: pillow>=6.2.0 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (8.2.0)
    Requirement already satisfied: kiwisolver>=1.0.1 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (1.3.1)
    Requirement already satisfied: numpy>=1.15 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (1.20.2)
    Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=2.0.3 in c:\users\mpbailon\anaconda\lib\site-packages (from matplotlib->mapboxgl->mapboxgl_notebook) (2.4.7)
    Requirement already satisfied: six in c:\users\mpbailon\anaconda\lib\site-packages (from cycler>=0.10->matplotlib->mapboxgl->mapboxgl_notebook) (1.16.0)
    


```python
import plotly.graph_objects as go
import os
```


```python
mapbox_access_token = "pk.eyJ1IjoiZXJuZXN0b3BlcmV6Y2hhdmV6IiwiYSI6ImNrZmN1czBucTAwOGcyc21xbzAzZ2hzaDQifQ.Xvu_MExeIsrbRrloPQAGhw"

fig = go.Figure()


fig.add_trace(go.Scattermapbox( #Se geolocalizan y marcan las centrales en operación
        lat=latitud_operacion,
        lon=longitud_operacion,
        mode='markers',
        name = "Central en operación",
        marker=go.scattermapbox.Marker(
            size=7, color="red"
        ),
        text=centrales_en_operacion
    ))

fig.add_trace(go.Scattermapbox( #Se geolocalizan y marcan las centrales en prueba
        lat=latitud_potencial,
        lon=longitud_potencial,
        mode='markers',
        name = "Central en construcción",
        marker=go.scattermapbox.Marker(
            size=5, color="blue"
        ),
        text=centrales_potencial
    ))


fig.add_trace(go.Scattermapbox( #Se geolocalizan y marcan las estaciones meteorológicas
        lat=["16.5470194", "21.1374778","18.594975", "21.6566889", "29.020575", "32.4806861", "25.0221806"],
        lon=["-94.95578611111111", "-89.78537777777778", "-97.93705277777778", "-101.71536666666667", "-106.9522", 
             "-116.11296111", "-98.08738333333334"],
        mode='markers',
        name = "Torre metereológica",
        marker=go.scattermapbox.Marker(
            size=9, color="black"
        ),
         text=["M4 CERTE", "M2 Mérida", "M7 Tepexi","M5 Ojuelos", "M3 Ciudad Cuauhtemoc", "M1 La Rumorosa", "M6 San Fernando"]
    ))

fig.update_layout(
    autosize=True,
    hovermode='closest',
    title={
        'text': "Centrales de energía eólica en México.",
        'y':0.86,
        'x':0.43,
        'xanchor': 'center',
        'yanchor': 'top'},
    font=dict(
        family="Times New Roman",
        size=16,
        color="Black",
        ),
    mapbox=dict(
        accesstoken=mapbox_access_token,
        bearing=0,
        center=dict(
            lat=24, #Lat y lon donde se centra el mapa
            lon=-100
        ),
        pitch=10,
        zoom=3.7
    ),
   
)

fig.show()


```


<div>


            <div id="dc261139-b8d5-49ad-be5a-ab265dce4c1d" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};

                if (document.getElementById("dc261139-b8d5-49ad-be5a-ab265dce4c1d")) {
                    Plotly.newPlot(
                        'dc261139-b8d5-49ad-be5a-ab265dce4c1d',
                        [{"lat": [16.484234, 16.612269, 16.587181, 16.581341, 27.976174, 16.60175, 20.97608, 25.970092, 16.497802, 16.546048, 23.329936, 16.537189, 32.59718, 31.3433, 16.564282, 16.611278, 16.584106, 16.440613, 16.528698, 16.184982, 16.536994, 16.530775, 21.853772, 25.683056, 16.444821, 16.547534, 16.586349, 16.411529, 16.545581, 32.497764, 16.528297, 16.577272, 18.815595, 16.496007, 25.892214, 25.892214, 21.864167, 25.697523, 23.389212, 23.789167, 23.877375], "lon": [-94.994522, -94.810514, -94.794464, -94.747944, -114.067172, -94.834917, -86.862118, -98.328577, -94.809892, -94.828453, -101.268156, -94.991577, -116.0787, -113.566783, -94.721195, -95.004556, -94.733927, -94.991183, -94.790108, -93.939629, -94.961348, -94.960956, -101.599417, -100.640556, -95.058775, -94.830467, -95.001612, -94.955415, -94.963352, -116.089826, -94.932617, -94.82351, -97.562787, -94.999971, -98.786667, -98.786667, -101.593333, -101.403103, -98.990885, -98.969444, -101.736536], "marker": {"color": "red", "size": 7}, "mode": "markers", "name": "Central en operaci\u00f3n", "text": ["Bii Nee Stipa I. Capacidad instalada (MW): 26.35", "Ce Oaxaca Cuatro. Capacidad instalada (MW): 102.0", "Ce Oaxaca Dos. Capacidad instalada (MW): 102.0", "Ce Oaxaca Tres. Capacidad instalada (MW): 102.0", "Guerrero Negro (Puerto Viejo). Capacidad instalada (MW): 0.6", "La Venta. Capacidad instalada (MW): 84.2", "Yuumil Ik. Capacidad instalada (MW): 1.5", "Compa\u00f1\u00eda E\u00f3lica de Tamaulipas. Capacidad instalada (MW): 54.0", "Parque e\u00f3lico Piedra Larga Fase 2. Capacidad instalada (MW): 90.0", "E\u00f3licos Mexicanos de Oaxaca I. Capacidad instalada (MW): 137.5", "Dominica Energ\u00eda Limpia. Capacidad instalada (MW): 200.0", "El\u00e9ctrica del Valle de M\u00e9xico. Capacidad instalada (MW): 67.5", "Energ\u00eda Sierra Ju\u00e1rez. Capacidad instalada (MW): 156.0", "Energ\u00eda Sonora PPE. Capacidad instalada (MW): 2.0", "Energias Ambientales de Oaxaca. Capacidad instalada (MW): 102.0", "Energ\u00edas Renovables La Mata, S. A. P. I. de C. V.. Capacidad instalada (MW): 102.0", "Energ\u00edas Renovables Venta III. Capacidad instalada (MW): 102.85", "Eoliatec del Istmo. Capacidad instalada (MW): 164.0", "Eoliatec del Pac\u00edfico. Capacidad instalada (MW): 160.0", "E\u00f3lica de Arriaga. Capacidad instalada (MW): 32.0", "E\u00f3lica Dos Arbolitos, S.A. P. I. de C. V.. Capacidad instalada (MW): 70.0", "E\u00f3lica El Retiro. Capacidad instalada (MW): 74.0", "Los Altos. Capacidad instalada (MW): 64.6", "E\u00f3lica Santa Catarina. Capacidad instalada (MW): 22.0", "E\u00f3lica Zopiloapan (Bii Nee Stipa III). Capacidad instalada (MW): 70.0", "Eurus. Capacidad instalada (MW): 250.5", "Fuerza E\u00f3lica del Istmo. Capacidad instalada (MW): 80.0", "Fuerza y Energ\u00eda BII HIOXO. Capacidad instalada (MW): 234.0", "Instituto de Investigaciones El\u00e9ctricas. Capacidad instalada (MW): 5.0", "Municipio de Mexicali. Capacidad instalada (MW): 10.0", "Parques Ecol\u00f3gicos de M\u00e9xico. Capacidad instalada (MW): 101.9", "PE Ingenio, S. de R. de C. V.. Capacidad instalada (MW): 49.5", "Pier II Quecholac Felipe \u00c1ngeles, S. A. de C. V.. Capacidad instalada (MW): 66.0", "Stipa Nayaa (Bii Nee Stipa II). Capacidad instalada (MW): 74.0", "Ventika, S. A. de C. V.. Capacidad instalada (MW): 126.0", "Ventika 11, S. A. de C. V.. Capacidad instalada (MW): 126.0", "Energ\u00eda Limpia de Palo Alto, S. de R. L. de C. V.. Capacidad instalada (MW): 129.0", "E\u00f3lica de Coahuila, S.A de C.V. Capacidad instalada (MW): 200.6", "E\u00f3lica Tres Mesas,S de R.L de C.V. Capacidad instalada (MW): 62.7", "C\u251c\u00a1a Eoloel\u251c\u00aectrica de Cd. Victoria,S:A de C:V. Capacidad instalada (MW): 50.0", "Vientos del Altiplano, S. de R. L. de C. V.. Capacidad instalada (MW): 140.0"], "type": "scattermapbox"}, {"lat": [25.7922333, 21.146367, 20.980783000000002, 20.585333000000002, 19.87935, 21.146367, 21.88267, 21.400167, 23.618103, 23.617971999999998, 25.941694000000002, 23.043426, 16.477788, 29.386125, 21.253767, 31.3433, 21.855949, 25.405213, 24.321637, 21.542227, 21.699319, 21.346633, 21.373587, 21.28085, 20.410603, 19.968895999999997, 21.714299, 20.941536, 23.429467000000002, 26.104693, 31.295700000000004, 19.052646, 21.18217, 21.2921, 21.2793, 21.442683, 21.270241, 21.267166999999997, 16.50276, 16.22846, 22.6125666, 21.569805, 25.192242999999998, 21.874311, 25.511200000000002, 21.837249999999997, 25.461245999999996, 21.724183, 31.072069999999997, 26.621261999999998, 28.984009999999998, 29.005143000000004, 18.819669, 18.63261, 32.602694, 16.582689, 25.436296, 32.499167, 32.584133, 21.2671666667, 21.7244333333, 25.8181666667, 25.906033333299998, 29.730466666700003, 24.5217833333, 25.4139666667, 16.56225, 26.350033333299997, 20.89105, 24.647861, 25.463786, 23.331191000000004, 23.399327, 29.605983000000002, 21.278593], "lon": [-101.61581600000001, -89.131967, -99.70098300000001, -99.10740000000001, -96.59285, -89.131967, -101.531484, -100.512333, -98.903689, -98.905472, -98.22788299999999, -102.05149, -94.98897400000001, -101.080778, -89.61625, -113.56678, -101.38050199999999, -101.991452, -104.810176, -101.68624799999999, -101.69784399999999, -100.49, -88.946423, -89.43811699999999, -100.367793, -96.597746, -101.49498100000001, -102.226477, -98.97550100000001, -100.13234600000001, -115.426, -96.05458300000001, -88.938316, -88.84331700000001, -88.8044, -87.994366, -89.252772, -89.187, -94.976694, -93.8949, -102.3690666, -101.33776, -97.950883, -101.265345, -100.959196, -101.27635, -101.974312, -101.81141600000001, -110.091299, -100.877536, -101.20710100000001, -101.292293, -97.38013799999999, -97.312061, -116.078056, -95.187086, -100.82513200000001, -116.10529999999999, -115.930683, -89.187, -101.74891666699999, -98.2280333333, -98.45660000000001, -101.648983333, -99.1548833333, -102.00281666699999, -94.8910666667, -99.28044999999999, -88.80559, -99.18669899999999, -98.57834199999999, -98.824562, -98.977438, -101.701179, -89.414738], "marker": {"color": "blue", "size": 5}, "mode": "markers", "name": "Central en construcci\u00f3n", "text": ["AE Mex Global. Capacidad instalada (MW): 96.0", "Aldener ADM,  (Central Parque E\u251c\u2502lico Chacabal II) (gen). Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables de M\u251c\u00aexico, Central Cadereyta (gen). Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables de M\u251c\u00aexico, Central Cardonal (gen). Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables de M\u251c\u00aexico, Central Juchique (gen). Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables de M\u251c\u00aexico, Central Parque E\u251c\u2502lico Chacabal (gen). Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables De M\u251c\u00aexico, Central Pinos. Capacidad instalada (MW): 30.0", "Aldesa Energ\u251c\u00a1as Renovables de M\u251c\u00aexico, Planta San Luis de la Paz (gen). Capacidad instalada (MW): 30.0", "Compa\u251c\u2592\u251c\u00a1a E\u251c\u2502lica Pr\u251c\u00edxedis. Capacidad instalada (MW): 58.0", "Compa\u251c\u2592\u251c\u00a1a E\u251c\u2502lica Vicente Guerrero (Central Vicente Guerrero). Capacidad instalada (MW): 60.0", "Delaro. Capacidad instalada (MW): 96.0", "Energ\u251c\u00a1a De Los Hern\u251c\u00edndez. Capacidad instalada (MW): 30.0", "Energ\u251c\u00a1a E\u251c\u2502lica del Sur. Capacidad instalada (MW): 396.0", "Energ\u251c\u00a1a Limpia De Amistad. Capacidad instalada (MW): 200.0", "Energ\u251c\u00a1a Renovable de la Pen\u251c\u00a1nsula (gen). Capacidad instalada (MW): 92.4", "Energ\u251c\u00a1a Sonora PPE. Capacidad instalada (MW): 2.0", "Energ\u251c\u00a1a Villa De Arriaga. Capacidad instalada (MW): 94.0", "Energ\u251c\u00a1a y Proyectos E\u251c\u2502licos. Capacidad instalada (MW): 50.0", "Energ\u251c\u00a1as Renovables de Durango. Capacidad instalada (MW): 120.7", "E\u251c\u2502lica Cerritos. Capacidad instalada (MW): 76.0", "E\u251c\u2502lica Chinampas. Capacidad instalada (MW): 64.0", "E\u251c\u2502lica De Guanajuato. Capacidad instalada (MW): 63.0", "E\u251c\u2502lica del Golfo 1 (Aut). Capacidad instalada (MW): 40.949999999999996", "E\u251c\u2502lica del Mayab, S. A. P. I. de C. V.. Capacidad instalada (MW): 70.0", "Parque E\u251c\u2502lica Huimilpan. Capacidad instalada (MW): 30.0", "E\u251c\u2502lica Los Altos, Parque E\u251c\u2502lico Coyoles. Capacidad instalada (MW): 50.0", "E\u251c\u2502lica Los Altos, Parque E\u251c\u2502lico El Vigil. Capacidad instalada (MW): 40.0", "E\u251c\u2502lica San Juli\u251c\u00edn. Capacidad instalada (MW): 40.0", "E\u251c\u2502lica Tres Mesas 3 (gen). Capacidad instalada (MW): 49.5", "Eolicse. Capacidad instalada (MW): 40.0", "Fuerza E\u251c\u2502lica de San Mat\u251c\u00a1as. Capacidad instalada (MW): 30.0", "Fuerza Viento Papalopan. Capacidad instalada (MW): 40.0", "Fuerza Y Energ\u251c\u00a1a Limpia De M\u251c\u00aexico. Capacidad instalada (MW): 30.0", "Fuerza y Energ\u251c\u00a1a Limpia de M\u251c\u00aexico, S. de R. L. de C. V. (Central Temax I). Capacidad instalada (MW): 75.6", "Fuerza y Energ\u251c\u00a1a Limpia de M\u251c\u00aexico, S. de R. L. de C. V. (Central Temax II). Capacidad instalada (MW): 75.6", "Fuerza y Energ\u251c\u00a1a Limpia de Tizim\u251c\u00a1n. Capacidad instalada (MW): 75.6", "Fuerza y Energ\u251c\u00a1a Limpia de Yucat\u251c\u00edn. Capacidad instalada (MW): 70.0", "Fuerza y Energ\u251c\u00a1a Limpia de Yucat\u251c\u00edn, S. de R. L. de C. V. (Central Sinanch\u251c\u00ae I). Capacidad instalada (MW): 75.6", "Generadora De Energ\u251c\u00a1a Del Istmo. Capacidad instalada (MW): 2.0", "Generadores E\u251c\u2502licos de Mexico. Capacidad instalada (MW): 10.0", "Gestamp Wind M\u251c\u00aexico II. Capacidad instalada (MW): 82.5", "Green Hub, Central El Roble. Capacidad instalada (MW): 24.0", "Grupo Soluciones en Energ\u251c\u00a1a Renovable Soe. Capacidad instalada (MW): 161.0", "Iberdrola Renovables Del Baj\u251c\u00a1o. Capacidad instalada (MW): 105.0", "Iberdrola Renovables Norte. Capacidad instalada (MW): 50.0", "Notus Energ\u251c\u00a1a M\u251c\u00aexico. Capacidad instalada (MW): 250.0", "Operadora E\u251c\u2502lica Mexicana. Capacidad instalada (MW): 300.0", "Parque E\u251c\u2502lico Ci\u251c\u00aenega de Mata. Capacidad instalada (MW): 200.0", "Parque E\u251c\u2502lico De Lecias. Capacidad instalada (MW): 103.49999999999999", "Parque E\u251c\u2502lico El Mezquite (gen). Capacidad instalada (MW): 250.0", "Parque E\u251c\u2502lico La Carabina I. Capacidad instalada (MW): 200.0", "Parque E\u251c\u2502lico La Carabina Ii. Capacidad instalada (MW): 150.0", "Parque Industrial de Energ\u251c\u00a1a Renovable. Capacidad instalada (MW): 150.0", "PIER IV. Capacidad instalada (MW): 150.0", "MPG Rumorosa. Capacidad instalada (MW): 72.0", "Secretar\u251c\u00a1a de la Defensa Nacional. Capacidad instalada (MW): 15.0", "Viento De Bella Uni\u251c\u2502n. Capacidad instalada (MW): 50.0", "Viga Solar Baja, S. A. P. I. de C. V. (Central La Rumorosa I). Capacidad instalada (MW): 57.5", "Viga Solar Baja, S. A. P. I. de C. V. (Central La Salada I). Capacidad instalada (MW): 46.0", "Fuerza y Energ\u251c\u00a1a Limpia de Kukulk\u251c\u00edn, S. A. de C. V.. Capacidad instalada (MW): 75.6", "E\u251c\u2502lica Chinampas, S. A. P. I. de C. V.. Capacidad instalada (MW): 37.400000000000006", "Energ\u251c\u00a1a Renovable del Istmo II, S. A. de C. V.. Capacidad instalada (MW): 168.0", "Parque Salitrillos, S. A. de C. V.. Capacidad instalada (MW): 100.0", "Desarrollo de Fuerzas Renovables, S. de R. L. de C. V.. Capacidad instalada (MW): 99.0", "E\u251c\u2502lica Buenos Aires, S. de R. L. de C. V.. Capacidad instalada (MW): 300.0", "Parques E\u251c\u2502licos de Mexico S.A. de C.V.. Capacidad instalada (MW): 200.0", "E\u251c\u2502lica de Oaxaca, S. A. P. I. de C. V.. Capacidad instalada (MW): 252.0", "EPM E\u251c\u2502lica 24, S. A. de C. V.. Capacidad instalada (MW): 131.1", "Iberia Renovables Tunk\u251c\u00eds, S. A. P. I. de C. V.. Capacidad instalada (MW): 70.0", "E\u251c\u2502lica Guadalupe, S. de R. L. de C. V.. Capacidad instalada (MW): 300.0", "Desarrollo de Fuerzas Renovables (Central Dolores), S. de R. L. de C. V.. Capacidad instalada (MW): 269.0", "E\u251c\u2502lica Mesa La Paz, S. de R. L. de C. V.. Capacidad instalada (MW): 300.0", "E\u251c\u2502lica Tres Mesas 4, S. de R. L. de C. V.. Capacidad instalada (MW): 95.7", "Desarrollo de Fuerzas Renovables (Central Energ\u251c\u00a1a Limpia de Amistad 3), S. de R. L. de C. V.. Capacidad instalada (MW): 99.0", "E\u251c\u2502lica del Golfo 4, S. A. de C. V.. Capacidad instalada (MW): 88.0"], "type": "scattermapbox"}, {"lat": ["16.5470194", "21.1374778", "18.594975", "21.6566889", "29.020575", "32.4806861", "25.0221806"], "lon": ["-94.95578611111111", "-89.78537777777778", "-97.93705277777778", "-101.71536666666667", "-106.9522", "-116.11296111", "-98.08738333333334"], "marker": {"color": "black", "size": 9}, "mode": "markers", "name": "Torre metereol\u00f3gica", "text": ["M4 CERTE", "M2 M\u00e9rida", "M7 Tepexi", "M5 Ojuelos", "M3 Ciudad Cuauhtemoc", "M1 La Rumorosa", "M6 San Fernando"], "type": "scattermapbox"}],
                        {"autosize": true, "font": {"color": "Black", "family": "Times New Roman", "size": 16}, "hovermode": "closest", "mapbox": {"accesstoken": "pk.eyJ1IjoiZXJuZXN0b3BlcmV6Y2hhdmV6IiwiYSI6ImNrZmN1czBucTAwOGcyc21xbzAzZ2hzaDQifQ.Xvu_MExeIsrbRrloPQAGhw", "bearing": 0, "center": {"lat": 24, "lon": -100}, "pitch": 10, "zoom": 3.7}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "Centrales de energ\u00eda e\u00f3lica en M\u00e9xico.", "x": 0.43, "xanchor": "center", "y": 0.86, "yanchor": "top"}},
                        {"responsive": true}
                    ).then(function(){

var gd = document.getElementById('dc261139-b8d5-49ad-be5a-ab265dce4c1d');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>


savefig
