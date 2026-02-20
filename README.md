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
