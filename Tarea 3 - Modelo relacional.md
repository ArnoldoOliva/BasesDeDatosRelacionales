### UANL
### FCFM, MCD

## Bases de datos relacionales

#### Modelo relacional:

Siguiendo con la base de datos de la ENIGH 2020, se presenta a continuación su modelo de relaciones:

**Viviendas (_id-viv_, tipo-viv, mat-pisos, num-cuarto, disp-agua, disp-elect, tenencia, renta, tot-resid,tam_loc, factor)**

**Hogares (_id-viv-hog_, acc-alim2, celular, conex-inte, num-auto, num-compu, tarjeta, negcua, est-alim, est-trans, id_viv)**

**Personas (_id-viv-hog-per_, sexo, edad, padre-hog, nivelaprob, edo-conyug, segsoc, hor-1, aten-sal,trabajo-mp, prob-mes, id_viv, id_viv_hog)**

**Trabajos (_id_, subor, indep, personal, htrab, clas-emp, tam-emp, tiene-suel, tipoact, id_viv, id_viv_hog, id_viv_hog_per)**

**Ingresos (_id_,	clave, ing-tri, id_viv, id_viv_hog, id_viv_hog_per)**

**GastosPersona (_id_, clave, mes_dia, frec-rem, forma-pag1, cantidad, costo, gasto-tri, gas-nm-tri, id_viv,id_viv_hog, id_viv_hog_per)**







Este modelo relacional se ve en forma de diagrama en el archivo *"Diagrama relacion"*