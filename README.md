# 16.Marzo.16.Ejercicio
#### Generar 4 objetos con datos aleatorios y que tengan 60 datos
### dato 1 de n?mero de profesionista (mill)rango de 5 a 8
### dato 2 crec pib rango de 0 a 5
### dato 3 porcentaje de ocupados rango de 40 a 60
### dato 4 porcentaje de desocupados rango de 3 a 8
#### 1) una vez que generen los datos hacer un data frame de los 4 objetos
#### 2) mostrar en consola los primeros 12 y ultimos 12 datos
#### 3) convertir los objetos en series de tiempo desde el data frame comezando en 2010 y son datos mensuales
#### 4) graficar los profesionistas y ocupados en la misma imagen
#### 5) graficar pib y desocupados en la misma imagen
#### 6) graficar todas juntas
### 7) creaR serie de tiempo multiple!!!!8
#### 8 ) graficar serie de tiempo multiple 
#### 9 ) dividir serie de tiempo y graficar solo el ultimo año...
#### 8 ) analizar las graficas ( si hay alguna tendencia o variacion estacional) (investigar)

prof<-sample(5000:8000, 60, replace=F)
cpib<-sample(0:5, 60, replace=T)
pocup<-sample(40:60, 60, replace=T)
pdesocup<-sample(3:8, 60, replace=T)
datos<-data.frame(prof,cpib,pocup,pdesocup)
c1<-datos[1:12,1:4]
c2<-datos[49:60,1:4]
tabla<-rbind(c1,c2)
tabla
serie<-ts(datos,start=c(2010,1),freq=12)
class(serie)
layout(1:2)
plot(prof, main="Profecionistas", xlab = "años", ylab ="numero de personas", 
     col="red" )
plot(pocup, main="Porcentaje Ocupados", xlab = "años", ylab ="numero de personas", 
     col="blue" )
layout(1:2)
plot(pib, main="Crecimiento del PIB", xlab = "años", ylab ="numero de personas", 
     col="orange" )
plot(pdesocup, main="Porcentaje Desocupados", xlab = "años", ylab ="numero de personas", 
     col="chartreuse" )
layout(1:3)
plot(prof, main="Profecionistas", xlab = "años", ylab ="numero de personas", 
     col="red" )
plot(pocup, main="Porcentaje Ocupados", xlab = "años", ylab ="numero de personas", 
     col="blue" )
plot(pib, main="Crecimiento del PIB", xlab = "años", ylab ="numero de personas", 
     col="orange" )
plot(pdesocup, main="Porcentaje Desocupados", xlab = "años", ylab ="numero de personas", 
     col="chartreuse" )
prof1<-ts(serie[,1], start = 2010,freq=12)
cpib1<-ts(serie[,2], start = 2010,freq=12)
pocup1<-ts(serie[,3], start = 2010,freq=12)
pdesocup1<-ts(serie[,4], start = 2010,freq=12)
seriemultiple <- ts.intersect(prof1,cpib1,pocup1,pdesocup1)
plot(seriemultiple, main="Serie de tiempo Multiple", xlab = "años", ylab ="numero de personas", 
     col="gold" )
seriemultiple10.13<-window(seriemultiple,start=c(2010,1), end=c (2013,12))
seriemultiple14.15<-window(seriemultiple,start=c(2014,1), end=c (2014,12))
plot(seriemultiple14.15, main="Serie de tiempo multiple", xlab = "años", ylab ="numero de personas", 
     col="blue" )
plot(seriemultiple10.13, main="serie de tiempo multiple", xlab = "años", ylab ="numero de personas", 
     col="red" )
start(seriemultiple); end(seriemultiple)

### Para analizar si hay tendencia se utiliza el metodo de minimo cuadrados,
## y para saber si tiene una variacion estacional se utiliza la tecnica de promedios moviles.
