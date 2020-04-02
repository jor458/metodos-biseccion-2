
Biseccion 1
#Realizado en python 3.x
from math import sin,cos,tan,asin,acos,atan,sqrt,log,exp
from math import sinh,cosh,tanh,asinh,acosh,atanh
print('Metodo de Bisseccion\n')
ec=input('De la funcion a resolver: ')  
x1=float(input('de el extremo inferior del intervalo aproximado: '))
x2=float(input('de el extremo superior del intervalo aproximado: '))
errordeseado=float(input('De el error deseado: '))
 

def f(x):
    return eval(ec)

 
while True:
    xmed=(x1+x2)/2
    fxmed=f(xmed)
    if fxmed==0.0:
        break
 
    if (f(x1)*f(xmed))<0:
        x1=x1
        x2=xmed
    else:
        x1=xmed
        x2=x2
    error=abs(x2-x1)
    if error<errordeseado:
        break
 

print ('La raíz es',xmed)
input(' ')
 
Biseccion 2
#!/usr/bin/python
import evaluar
from pylab import *
from Numeric import *
 
def biseccion(a, b, TOL, N):
    evaluar.dicc_seguro['x']=a
    fa = eval(evaluar.funcion, {"__builtins__":None}, evaluar.dicc_seguro)
 
    vectorx = zeros(N, Float64)
    vectory = zeros(N, Float64)
 
    i = 1
    while i<=N :
        p = (a+b)/2.0
        vectorx[i-1] = p
        evaluar.dicc_seguro['x']=p
        fp = eval(evaluar.funcion, {"__builtins__":None}, evaluar.dicc_seguro)
        vectory[i-1]=fp
        if (fp == 0.0) or ((b-a)/2.0)<tol:
            print "La raiz buscada es: ",p, "con", i-1, "iteraciones"
            break
        i = i+1
        if (fa*fp)>0 :
            a = p
        else :
            b = p
 
    return [vectorx, vectory]
 
def dibujar(a,b, TOL, N):
  x = arange(a,b,0.1)
  vectores=biseccion(a, b, TOL, N)
 
  subplot(211)
  plot(x, eval(evaluar.funcion), linewidth=1.0)
  xlabel('Abcisa')
  ylabel('Ordenada')
  title('Metodo Biseccion con f(x)=' + evaluar.funcion)
  grid(True)
  axhline(linewidth=1, color='r')
  axvline(linewidth=1, color='r')
 
  subplot(212)
  plot(vectores[0], vectores[1], 'k.')
  xlabel('Abcisa')
  ylabel('Ordenada')
  grid(True)
  axhline(linewidth=1, color='r')
  axvline(linewidth=1, color='r')
 
  show()
 
biseccion 3
__author__ =  ' jboris '

ERROR  =  1E-6
# Entradas
ec =  raw_input ( ' f (x): ' )
x0 =  float ( raw_input ( ' x0: ' ))
x1 =  float ( raw_input ( ' x1: ' ))
# Proceso
f0 =  eval (ec, { ' x ' : x0}) # f (x0)
f1 =  eval (ec, { ' x ' : x1}) # f (x1)
f2 =  1E10
si f0 * f1 <  0 :
    mientras que  abs (f2) >  ERROR :
        x2 = (x0 + x1) /  2
        f2 =  eval (ec, { ' x ' : x2}) # f (x2)
        si f1 * f2 <  0 :
            x0 = x2
        si f0 * f2 <  0 :
            x1 = x2
    respuesta = { ' x ' : x2}
else :
    respuesta =  ' Datos incorectos '
# Salidas
imprimir respuesta

 
biseccion 4

#--------------------------------------------------------------
#   Programa que utiliza el metodo de Biseccion para el calculo
#   de raices de un polinomio de n grado
#
#   PROGRAMA        :       Biseccion.py
#   PROGRAMADOR     :       Cruz Gomez Jovanny Pablo
#   LENGUAJE        :       Python
#   FECHA           :       03 de Marzo de 2012
#---------------------------------------------------------------


import os       
import math


#---------------------------------------------------------------
# Funcion que muestra el titulo del programa
#---------------------------------------------------------------
def titulo():
    os.system("CLS")
    print "Metodo de biseccion\n"


#---------------------------------------------------------------
# Funcion que evalua f(x) con el metodo de Horner
#---------------------------------------------------------------
def f(coeficientes, grado, valor):
    resultado = coeficientes[0]
    i = 1


    while(i <= grado):
        resultado = (resultado * valor) + coeficientes[i]
        i += 1


    return resultado
    
#---------------------------------------------------------------
# FUNCION QUE CALCULA Mx
#---------------------------------------------------------------
def Mx(a, b):
    return (a + b) / 2


#---------------------------------------------------------------
# METODO DE BISECCION
#---------------------------------------------------------------
def biseccion(coeficientes, grado, iInicial, iFinal):
    a = iInicial
    b = iFinal
    nIteraciones = math.ceil((math.log(b - a) - math.log(0.00001)) / math.log(2))


    titulo()


    print "{0}\t{1}\t{2}\t{3}\t{4}".format('n', 'a', 'b', 'Mx', 'f(Mx)f(a)')


    i = 1
    while(i <= nIteraciones):
        x = Mx(a, b)
        Fx = f(coeficientes, grado, x)
        Fa = f(coeficientes, grado, a)


        condicion = Fx * Fa


        print i, "\t{:.4}\t{:.4}\t{:.4}\t{:.4}".format(a, b, x, condicion)


        if(condicion > 0):
            a = x
        elif(condicion < 0):
            b = x
        else:
            x = x


        i += 1
    print "\nLa raiz encontrada es: {0}\n".format(x)


#---------------------------------------------------------------
#Programa principal
#---------------------------------------------------------------


consulta = '1'
while(consulta != '0'):
    os.system("COLOR F0")
    titulo()


    grado = int(raw_input("Grado de ecuacion: "))   
    print                                                  
    iInicial = float(raw_input("Intervalo inicial: "))      
    iFinal = float(raw_input("Intervalo final: "))         


    titulo()


    coeficientes = []       


    i = grado
    while(i >= 0):                                              
        cof = float(raw_input("Ingresa x^{0}: ".format(i)))     
        coeficientes.append(cof)                                
        i -= 1                                                   


    biseccion(coeficientes, grado, iInicial, iFinal)


    print
    consulta = raw_input("Para salir presiona 0, sino otra tecla: ")

 
biseccion 5
#Función para polinomios
def poli(x):
      y=pow(x,2)-(3*x)-4
      return (y)
#Programa principal
print "Este programa encuentra una raíz, por el método de bisección"
xi=float(raw_input('Introduce el valor de xi'))
xs=float(raw_input('Introduce el valor de xs'))
error=float((raw_input('Introduce el error')))
xa=(xi+xs)/2.0
i=0
print('{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}'.format('i','xi','xs','xa','signo','cambio','error'))
while abs(poli(xa)) > error:
    i=i+1
    print('{:^10}{:^10.4f}{:^10.4f}{:^10.4f}{:^10}{:^10}{:^10.4f}'.format(i,float(xi),float(xs),float(xa),signo,limite,float(poli(xa))))
    xa = (xi+xs)/2.0
    if poli(xi)*poli(xa) < 0:
        xs=xa
        signo="negativo"
        limite="superior"
    else:
        xi=xa
        signo="positivo"
        limite="inferior"
   
print"La raíz es: ",xa

 
biseccion 6
#Función para polinomios
def poli(x):
      y=pow(x,2)-(3*x)-4
      return (y)
#Programa principal
print "Este programa encuentra una raíz, por el método de bisección"
xi=float(raw_input('Introduce el valor de xi'))
xs=float(raw_input('Introduce el valor de xs'))
error=float((raw_input('Introduce el error')))
xa=(xi+xs)/2.0
i=0
print('{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}'.format('i','xi','xs','xa','signo','cambio','error'))
while abs(poli(xa)) > error:
    i=i+1
    print('{:^10}{:^10.4f}{:^10.4f}{:^10.4f}{:^10}{:^10}{:^10.4f}'.format(i,float(xi),float(xs),float(xa),signo,limite,float(poli(xa))))
    xa = (xi+xs)/2.0
    if poli(xi)*poli(xa) < 0:
        xs=xa
        signo="negativo"
        limite="superior"
    else:
        xi=xa
        signo="positivo"
        limite="inferior"
   
print"La raíz es: ",xa

 
biseccion 7
#!/usr/bin/python
 #-*- coding:utf-8 -*-
 
from math import *
 
ecuacion = raw_input('Ingrese la función a resolver: ')
 aValor = float(input('Ingrese el extremo inferior del intervalo: '))
 bValor = float(input('Ingrese el extremo inferior del intervalo: '))
 tolerancia = float(input('Ingrese la tolerancia del método: '))
 maximoIteraciones = int(input('Ingrese el máximo de iteraciones a realizar: '))
 
def f(x):
 return eval(ecuacion)
 
i = 0
 print "nn"
 print "tattbttf(a)ttf(b)ttcttf(c)n"
 fa = f(aValor)
 fb = f(bValor)
 
while i <= maximoIteraciones:
 cValor = (aValor + bValor)/2
 fc = f(cValor)
 print"t%.4ftt%.4ftt%.4ftt%.4ftt%.8ft%.4f" % (aValor, bValor, fa, fb, cValor, fc)
 
if (fc == 0.0) or abs(fc) < tolerancia:
 print "nnLa raíz buscada es: %.8f" %cValor, "con " + str(i) + " iteraciones"
 break
 
i = i +1
 
if ((fa*fc) maximoIteraciones):
 print "nnLa raíz buscada es: %.8f" %cValor, "con " + str(i-1) + " iteraciones"
 break
 
biseccion 8
def poli(x):
      y=pow(x,2)-(3*x)-4
      return (y)
#Programa principal
print "Este programa encuentra una raíz, por el método de bisección"
xi=float(raw_input('Introduce el valor de xi'))
xs=float(raw_input('Introduce el valor de xs'))
error=float((raw_input('Introduce el error')))
xa=(xi+xs)/2.0
i=0
print('{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}{:^10}'.format('i','xi','xs','xa','signo','cambio','error'))
while abs(poli(xa)) > error:
    i=i+1
    print('{:^10}{:^10.4f}{:^10.4f}{:^10.4f}{:^10}{:^10}{:^10.4f}'.format(i,float(xi),float(xs),float(xa),signo,limite,float(poli(xa))))
    xa = (xi+xs)/2.0
    if poli(xi)*poli(xa) < 0:
        xs=xa
        signo="negativo"
        limite="superior"
    else:
        xi=xa
        signo="positivo"
        limite="inferior"
   
print"La raíz es: ",xa

