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



Este modelo relación se ve en forma de diagrama en el sig link:
mermaid.ink/img/pako:eNqtVcGO2yAQ_RWLc1h5I22S9bUrbXuoVKmrHqpI0QQmDisDLuBot9n8ewfbibGVHCqtLwmPB7w3MwxHJqxEVjB0TwpKBzpbmyz7pQ4KjQSffXxwfrLZV1uCQ58V2Zp9sSbQLJo1a8nnuZ76A523Bq5z


### Operaciones de álgebra relacional

Estas relaciones permiten combinaciones entre sí mismas para analizar los datos. Algunas de las posibles operaciones que podrían surgir son:


**De selección:**

**1)**
π id-viv, tipo-viv, mat-pisos, num-cuarto, disp-agua, renta, tot-resid, tam-loc [σ mat-pisos <> 3 (Viviendas)]

 π id-viv, tipo-viv, mat-pisos, num-cuarto, disp-agua, renta, tot-resid, tam-loc  (Viviendas) [ mat-pisos<>3 ]

Con este ejercicio se está seleccionando todas las viviendas que no tienen algún acabado especial en el suelo (no cuentan con mosaicos, madera, etc.) Sería interesante ver las proporciones de las otras variables (tamaño localidad, número de cuartos, acceso al agua, renta mensual), cuando el suelo es tierra o cemento.


**2)** 
π id, personal, htrab, clas-emp, tam-emp, tipo-act, id_viv_hog_per   [ σ personal = 2 n σ tamp-emp >=7 (Trabajos) ]

π id, personal, htrab, clas-emp, tam-emp, tipo-act, id_viv_hog_per (Trabajos) [ personal=1 n tamp-emp>=7]

Lo que se esta haciendo en esta selección es trabajar con los registros donde la persona sea un empresario y tenga personal a su mando, y donde el tamaño de la empresa sea mayor o igual a 31 personas (mediana empresa), para analizar en la proyección mostrada las proporciones de horas trabajadas, clase de la empresa, tipo de actividad y tamaño de la empresa.

**3)**
σ negcua=1 (Hogares) n σ acc-alim2=1 (Hogares)

Hogares[ negcua=1 U acc-alim2=1 ]

Estaría interesante analizar las proporciones de las variables de Hogares cuando en dicho hogar se cuenta con un negocio propio, pero al mismo tiempo dicha familia haya quedado sin acceso a alimentos en esos 3 últimos 3 meses.



**De composición:**

**4)**

σ Personas.id_viv_hog_per = Ingresos.id_viv_hog_per (π sexo, edad, nivelaprob, hor_1, edo-conyug segsoc, prob-mes (Personas) **x** π clave ing-tri (Ingresos))

π sexo, edad, nivelaprob, hor_1, edo-conyug, segsoc, prob-mes (Personas)[ Personas.id_viv_hog_per = Ingresos.id_viv_hog_per ]π clave ing-tri (Ingresos)

Esta composición hace un join de las relaciones de Personas e Ingresos para poder analizar si puede haber una relación de sus ingresos en cantidad y tipo con su nivel educativo, edad, sexo, edo conyugal, entre otros.

