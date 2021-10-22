#Comenzamos instalando la libreria "dslabs" que servira para tomar bases de datos y enseguida la carga,os
install.packages("dslabs")
library(dslabs)

installed.packages()

#Caso de estudio: los asesinatos con armas en EE. UU.


#Data nos permite observar los sets de datos disponibles para practicar
data(co2)
summary(co2)

#Otras funciones
#seq crea una lista de números y sum los suma.
seq(1,5,0.5)
sum(1,2.3)

#data frame:

#como una tabla con filas que representan observaciones y con columnas que representan las diferentes variables recopiladas para cada observación. Los data frames son particularmente útiles para sets de datos porque podemos combinar diferentes tipos de datos en un solo objeto.
#Pueden tener acceso a este set de datos cargando el paquete dslabs y entonces utilizando la función data para cargar el set de datos murders :

#library(dslabs)
data(murders)
str(murders)
head(murders)
names(murders)
length(murders$abb)
summary(murders$population)
max(murders$population)


region <- murders$region
value <- murders$total
region <- reorder(region, value, FUN = sum)
levels(region)

#Las listas son útiles porque pueden almacenar cualquier combinación de diferentes tipos de datos. Pueden crear una lista utilizando la función lista así:


record <- list(name = "John Doe",
               student_id = 1234,
               grades = c(95, 82, 91, 97, 93),
               final_grade = "A")
               
class(record)   
               
#Podemos crear vectores usando la función c, que significa concatenar. Usamos c para concatenar entradas de la siguiente manera:


codes <- c(380, 124, 818)      
codes

#A veces es útil nombrar las entradas de un vector. Por ejemplo, al definir un vector de códigos de paises, podemos usar los nombres para conectar los dos:

codes <- c(italy = 380, canada = 124, egypt = 818)

names(codes)
sort(murders$total)
a <- murders$total

x <- c(31, 4, 15, 92, 65)
sort(x)
order(x)
murders$state[which.max(murders$population)]
murder_rate <- murders$total/ murders$population * 100000

##Creacion de una DataFrame

temp <- c(35, 88, 42, 84, 81, 30)
city <- c("Beijing", "Lagos", "Paris", "Rio de Janeiro",
          "San Juan", "Toronto")
          
city_temps <- data.frame(name = city, temperature = temp, celsius = 5/9 *(temp - 32))
city_temps
summary(city_temps)

## Suma de Euler 
eu <- seq(1,100)

euler <- data.frame(1/eu^2)
sum(euler)

ind <- murder_rate < 0.71
murders

murders$abb[ind]
murders$state[ind]
sum 


west <- murders$region == "West"
safe <- murder_rate <= 1

ind <- safe & west
murders$state[ind]

ind <- which(murders$state == "California")
murder_rate[ind]

ind

##Gràficos

x <- murders$population/ 10^6
y <- murders$total
plot(x, y)

##Tambièn se puede usar la funcion with:

with(murders, plot(population/ 10^6, total))

x <- murders$population
hist(x)

x <- with(murders, population)
hist(x)

boxplot(total ~  region, data = murders)

