### UANL
### FCFM, MCD

## Bases de datos relacionales

#### Modelo relacional:

Siguiendo con la base de datos de la ENIGH 2020, se presenta a continuación su modelo de relaciones:

**Viviendas (_id-viv_, tipo_viv, mat_pisos, num_cuarto, disp_agua, disp_elect, tenencia, renta, tot_resid,tam_loc, factor)**

**Hogares (_id-viv-hog_, acc_alim2, celular, conex_inte, num_auto, num_compu, tarjeta, negcua, est_alim, est_trans, id-viv)**

**Personas (_id-viv-hog-per_, sexo, edad, padre_hog, nivelaprob, edo_conyug, segsoc, hor_1, aten_sal,trabajo_mp, prob_mes, id_viv, id_viv_hog)**

**Trabajos (_id_, subor, indep, personal, htrab, clas_emp, tam_emp, tiene_suel, tipoact, id_viv, id_viv_hog, id_viv_hog_per)**

**Ingresos (_id_,	clave, ing_tri, id_viv, id_viv_hog, id_viv_hog_per)**

**GastosPersona (_id_, clave, mes_dia, frec_rem, forma_pag1, cantidad, costo, gasto_tri, gas_nm_tri, id_viv,id_viv_hog, id_viv_hog_per)**







Este modelo relacional se ve en forma de diagrama en el archivo *"Diagrama relacion"*