import time

def calcular_tiempo(funcion):
    def wrapper(*args, **kwargs):
        inicio = time.time()
        resultado = funcion(*args, **kwargs)
        fin = time.time()
        print(f"Tiempo de ejecución de {funcion.__name__}: {fin - inicio} segundos")
        return resultado
    return wrapper

@calcular_tiempo
def buscar_calificacion(matriz, alumno, materia):
    calificacion = matriz[alumno][materia]
    return calificacion

num_alumnos = 100
num_materias = 6
matriz_calificaciones = [[0] * num_materias for _ in range(num_alumnos)]

import random
for i in range(num_alumnos):
    for j in range(num_materias):
        matriz_calificaciones[i][j] = random.randint(0, 10)

alumno_buscar = 94  # índice 94 en Python (alumno 95)
materia_buscar = 4   # índice 4 en Python (materia 5)
calificacion_buscar = buscar_calificacion(matriz_calificaciones, alumno_buscar, materia_buscar)
print(f"Calificación del alumno {alumno_buscar + 1} en la materia {materia_buscar + 1}: {calificacion_buscar}")
