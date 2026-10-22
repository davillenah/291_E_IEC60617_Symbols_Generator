# iec60617-symbol-generator

Biblioteca de simbolos electricos para los plugins sld-generator y mld-generator. Version 0.4.16.

## Contenido

- src/sld-lv-symbol: simbolos unifilares de baja tension (SVG + DXF)
- src/sld-mv-symbol: simbolos unifilares de media tension (SVG + DXF)
- src/mld-lv-symbol: simbolos multifilares de baja tension (SVG + DXF)
- src/mld-mv-symbol: simbolos multifilares de media tension (pendiente)
- src/ssd-mv-symbol: biblioteca adicional de media tension (_library.svg)
- catalogo_simbolos.xlsx: catalogo con todos los simbolos y su imagen por biblioteca

Cada simbolo tiene un archivo `.svg` (editable) y un `.dxf` con el mismo nombre. El DXF trae un bloque con el nombre del archivo en mayusculas (por ejemplo `LV_MCB`), origen en el puerto superior, unidades en mm, textos Arial y atributos para los parametros variables con texto por defecto. Reglas de texto: el tag es el primer atributo de cada simbolo (Arial 2.5 mm, azul TRUECOLOR); los demas atributos van en Arial 1.7 mm negro (ACI 7); los textos fijos del simbolo van en Arial 1.7 mm azul TRUECOLOR (los tipo MCB, MCCB, etc. en Arial Black). Todas las entidades en capa 0 con grosor y tipo de linea ByLayer.

Simbolo nuevo en 0.3.0: `lv_cable_run` (tramo de cable con identificacion). Parametros variables: `cable_tag` (circuito / longitud), `cable_spec` (seccion) y `cable_insulation` (aislacion / norma).

## Version

- **0.4.16** – Nuevos símbolos MCCB sin extracción (basic y motorized) en SLD y MLD 1p–4p; catálogo Excel reconstruido con los 221 símbolos; referencias de archivo del catálogo corregidas.
- **0.4.15** – Catálogo: 42 entradas nuevas (variantes ACB/MCCB con drawout, LSIG y motorizado en MLD y SLD, y lv_cable_run); viewBox y size sincronizados con los SVG; puertos SLD sincronizados; catálogos JSON ordenados y uno por biblioteca (sld-lv, sld-mv, mld-lv, mld-mv); un único catalogo_simbolos.xlsx. Pendiente: 10 entradas MCCB basic/motorized sin SVG.
- **0.4.14** – Paso entre polos MLD = 10 mm (antes 12.5 mm): ejes de polo en x = 0, 10, 20, 30; celdas ACB/MCCB de 10 mm contiguas; cajas anchas (ATS, VFD, UPS, motor, generador, etc.) = 10 mm por polo; puertos, etiquetas, viewBox y DXF actualizados en los 72 archivos multipolo.
- **0.4.13** – Geometría real unificada en SVG/DXF MLD: celdas de protección ACB/MCCB (todas las variantes: drawout, LSIG, motorizado) de 10 mm de ancho en 1p/2p/3p/4p, centradas en el eje de polo de 12.5 mm; relé térmico 4.9 mm por polo; decoración (drawout, motor) y viewBox alineados igual en todos los polos; DXF y catálogos regenerados.
- 0.4.12: catalogo Excel con escala uniforme (4 px por mm) para todos los simbolos: antes cada imagen se ajustaba a una caja fija y los simbolos mas grandes se veian mas chicos; ahora filas y columnas se adaptan al tamano real (las celdas MV de gabinete, de 290 mm de alto, se reducen para entrar en la fila).
- 0.4.11: MLD actualizados segun los cambios SLD: contactor (contacto NA con arco), interruptor-seccionador (barra y circulo) y fusible (rectangulo sobre la linea) por polo, con enlace mecanico punteado; generador y motor con circulo de 10 mm; bornes inferiores a 15 mm; eliminados rotulos de tipo duplicados en 18 MLD. DXF y catalogos regenerados.
- 0.4.10: encuadre de textos en SLD y MLD: textos internos (A, V, W, M, G, 3~, I>, I>>, I>>>, I/Δ, kWh, VFD, ATS, etc.) centrados en su celda, circulo o caja; etiqueta de tipo (ACB, MCCB...) en Arial como el resto; corregidos MLD ACB LSIG (glifos duplicados o faltantes en algunos polos) y MLD ACB LSIG motorizado (flecha y puerto inferior dentro de la pila de celdas, ahora debajo, igual que el SLD); numeros de borne de los drawout separados de las flechas. En ACB/MCCB solo se movieron textos, no la geometria editada a mano. DXF y catalogos regenerados.
- 0.4.9: normalizacion de proporciones SLD (LV y MV) a la grilla de 2,5 mm: todos los circulos a diametro 10 mm (medidores A/V/W/var/cos/f, motores, generadores, lamparas, CT, VT, toroidal), cargas y cajas a 10 mm, alturas y anchos de reactores, reles, variador, UPS, arrancador suave, inversor, cargador EV, banco de capacitores, FV, etc. a multiplos de 2,5 mm; voltimetro rehecho (estaba roto). DXF y catalogos regenerados. Sin tocar ACB/MCCB. MLD pendiente.
- 0.4.8: simbolos SLD redibujados segun la norma IEC 60617 (assets/IEC_60617_Simbologia.pdf): contacto NA/NC, pulsadores NA/NC (actuador con "E"), contactor (arco), seccionador-fusible/interruptor-seccionador, seccionador (LV y MV), fusible (rectangulo), tomacorriente; DXF y catalogos regenerados. Pendiente de alinear: TC, rectificador, parada de emergencia, rele termico, SPD, reactancia, MCB/RCBO. Los simbolos editados a mano (ACB y MCCB) no se tocaron.
- 0.4.7: revision de los simbolos SLD (LV y MV): eliminados rotulos de tipo duplicados y superpuestos; rotulos mal derivados corregidos (CABLE IN/OUT, PE BAR, 3PH, TERM); parametros IEC agregados a los que faltaban (contactos, pulsadores, tierra, load box, conmutador, marcador trifasico, flechas de cable, medidores, selector, VPIS, seccionador de tierra, descargador); diametros normalizados (ct LV, vt LV, ct_toroidal MV, transformer_2w MV); DXF y catalogo regenerados. Los simbolos editados a mano (ACB y MCCB) no se tocaron.
- 0.4.6: matriz ACB completa en SLD y MLD (acb, acb_lsig, acb_motorized, acb_lsig_motorized, acb_drawout, acb_lsig_drawout, acb_motorized_drawout, acb_lsig_motorized_drawout). Nombre de drawout por geometria (flechas arriba y abajo). Bloque LSIG con etiquetas I>, I>>, I>>> y marcadores. Motorizado drawout con flecha inferior bajo el bloque de proteccion. Catalogo Excel con imagen -> SVG y nombre -> DXF.
- 0.4.5: simbolos ajustados a mano (ACB y MCCB drawout/motorizado) con DXF regenerados; nuevo simbolo mccb_lsig_drawout (MCCB con funciones LSIG).
- 0.4.4: drawout = flechas arriba y abajo (SLD y MLD); acb_motorized con flechas (drawout) y version sin flechas; parametros IEC 60617 por familia (capacidad, In, disparo, sensibilidad, relacion, potencia, etc.) a la izquierda del simbolo.
- 0.4.3: todas las etiquetas (TAG, tipo de equipo, parametros y MANUFACTURER) a la izquierda del simbolo, una debajo de otra (TAG arriba, MANUFACTURER abajo). Drawout = equipo con flechas arriba y abajo (acb_drawout, mccb_drawout); acb_motorized_drawout por nombre.
- 0.4.2: todos los simbolos tienen TAG y MANUFACTURER (SVG y DXF); el atributo cable_tag pasa a ser TAG; el texto CONTACTOR pasa a KM.
- 0.4.1: orden de etiquetas: TAG arriba, tipo de equipo debajo y MANUFACTURER al final (en los simbolos con columna de etiquetas). Equipos extraibles con sufijo `_drawout` en el nombre (acb_motorized). 
- 0.4.0: tag como primer atributo de cada simbolo (2.5 mm azul), resto de textos a 1.7 mm, textos fijos en azul TRUECOLOR, atributos en negro (ACI 7), SVG y DXF actualizados y catalogo regenerado.
- 0.3.0: simbolo lv_cable_run y catalogo en Excel.
- 0.2.0: salida DXF por bloques para todos los simbolos.
- 0.1.0: biblioteca inicial en SVG.
