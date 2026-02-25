# Taller1
import numpy as np

#Vectores
x_vector = np.array([2, 6, 2])
y_vector = np.array([2, 5, 2])

#Matrices
x_matrix = np.array([[2, 5, 2], [5,2, 6], [2, 7, 4]])
y_matrix = np.array([[5, 5, 1], [3, 4, 2], [5, 2, 4]])

#Coordenadas
x = 2
y = 3
z = 2

#Operaciones de vectores
sum = x_vector + y_vector
subs = x_vector - y_vector
dot = np.dot(x_vector, y_vector)
cross = np.cross(x_vector, y_vector)

#Operaciones de matrices
matrix_sum = x_matrix + y_matrix
matrix_subs = x_matrix - y_matrix
matrix_dot = x_matrix @ y_matrix
matrix_cross = np.cross(x_vector, y_vector)
y_inverse = np.linalg.inv(y_matrix)
# proof = y_matrix @ y_inverse
matrix_div = x_matrix @ y_inverse

#conversion de coordenadas rectangulares a cilindricas
r = np.sqrt(x**2 + y**2)
theta = np.atan2(y, x)

#conversion de coordenadas rectangulares a esfericas
rho = np.sqrt(x**2 + y**2 + z**2)
phi = np.arccos(z / rho)

temperatura = 25

R0 = 100.0  
A = 3.9083e-3
B = -5.775e-7
C = -4.183e-12

if temperatura >= 0:
  R_t = R0 * (1 + A * temperatura + B * temperatura**2)
else:
  R_t = R0 * (1 + A * temperatura + B * temperatura**2 + C * (temperatura - 100) * temperatura**3)

#Resultados
print(f'La suma es: {sum}')
print(f'La resta es: {subs}')
print(f'Producto punto: {dot}')
print(f'Producto cruz: {cross}')
print(x_matrix)
print(y_matrix)
print(matrix_dot)
print(matrix_cross)
print(matrix_sum)
print(matrix_subs)
print(y_inverse)
print(matrix_div)
print(f'Las coordenadas cilindricas son: ({r:.2f}, {theta:.2f}, {z})')
# print(rho)
# print(phi)
print(f'Las coordenadas esfericas son: ({rho}, {phi}, {theta})')
print(f'La resistencia de la PT100 a {temperatura}°C es: {R_t:.2f} Ohms')


angle_degrees = 90
angle_radians = np.radians(angle_degrees)

cos_theta = np.cos(angle_radians)
sin_theta = np.sin(angle_radians)
rotation_matrix_x = np.array([
    [1, 0, 0],
    [0, cos_theta, -sin_theta],
    [0, sin_theta, cos_theta]
])

cos_theta = np.cos(angle_radians)
sin_theta = np.sin(angle_radians)
rotation_matrix_y = np.array([
    [cos_theta, 0, sin_theta],
    [0, 1, 0],
    [-sin_theta, 0, cos_theta]
])

cos_theta = np.cos(angle_radians)
sin_theta = np.sin(angle_radians)
rotation_matrix_z = np.array([
    [cos_theta, -sin_theta, 0],
    [sin_theta, cos_theta, 0],
    [0, 0, 1]
])

print(f"Rotacion en x a {angle_degrees} grados:\n{rotation_matrix_x}\n")
print(f"Rotacion en y a {angle_degrees} grados:\n{rotation_matrix_y}\n")
print(f"Rotacion en z a {angle_degrees} grados:\n{rotation_matrix_z}\n")







# TallerParteB
#B1
# Realice un programa que calcule la potencia que consume un circuito ingresando por teclado el
# valor de corriente y voltaje.

V = int(input('Valor de voltaje '))
I = int(input('Valor de corriente '))
P = I * V
print(f'Valor de potencia {P:.2f}W')

=============================================================================================
#B2
# Realice un programa que calcule X números aleatorios en un rango determinado por el usuario.

import random

print('Generador de numero aleatorio')
N = int(input('Cantidad de numeros: '))
x = int(input('Desde: '))
y = int(input('Hasta: '))
for i in range(N):
  numero = random.randint(x, y)
  print(f'Numero aleatorio {i + 1}: {numero}')
=============================================================================================
# B3
# Realice un programa para el cálculo de volúmenes (Prisma, Pirámide, Cono truncado, Cilindro)
# donde el usuario pueda seleccionar el sólido y los parámetros de cada volumen.
import numpy as np

print('Calculador de volumen\nSelecionar solido:\n1. Prisma\n2. Pirámide\n3. Cono truncado\n4. Cilindro')
seleccion = int(input('Ingresar numero (ej: 1 para prisma): '))
#print(seleccion)
if seleccion == 1:
  l = int(input('Valor del largo: '))
  a = int(input('Valor del ancho: '))
  h = int(input('Valor de la altura: '))
  v = l * a * h
  print(f'El volumen del prisma es {v:.2f}m^3')

elif seleccion == 2:
  l = int(input('Valor del largo: '))
  a = int(input('Valor del ancho: '))
  h = int(input('Valor de la altura: '))
  v = (1 / 3) * l * a * h
  print(f'El volumen de la piramide es {v:2f}m^3')

elif seleccion == 3:
  h = int(input('Valor de la altura: '))
  R = int(input('Valor radio de la base mayor: '))
  r = int(input('Valor radio de la base menor: '))
  v = (1/3) * np.pi * h * (R**2 + R * r + r**2)
  print(f'El volumen del cono truncado es {v:.2f}m^3')

elif seleccion == 4:
  h = int(input('Valor de la altura: '))
  r = int(input('Valor del radio: '))
  v = np.pi * r**2 * h
  print(f'El volumen del cilindro es {v:.2f}m^3')

else:
  print('Numero fuera de rango')
=============================================================================================
# B4
# Realice un programa que le permita al usuario escoger entre robot Cilíndrico, Cartesiano y esférico,
# donde como respuesta a la selección conteste con el tipo y número de articulaciones que posee.

print('Articulaciiones robóticas')
print('1. Cilíndrico\n2. Cartesiano\n3. Esférico')
selec = int(input('Selecionar tipo de robot (ej: 1 para cilíndrico): '))

print('\nRespuesta:\n')
if selec == 1:
  print('Un robot cilíndrico tiene 3 articulaciones, una rotacional y dos prismáticas.')
elif selec == 2:
  print('Un robot cartesiano tiene 3 articulaciones prismáticas.')
elif selec == 3:
  print('Un robot esférico tiene 3 articulaciones, dos rotacionales y una prismatica.')
else:
  print('Numero fuera de rango')
=============================================================================================
# B5
# Escribir un programa que realice la pregunta ¿Desea continuar Si/No? y que no deje de hacerla
# hasta que el usuario teclee No.

while(1):
  resp = input('¿Desea continuar Si/No?')
  if resp == 'No':
    break
