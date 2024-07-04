# examen_extraordinaria_2023_2024_marta_nieto_romero
Ejercicio 4
# coche.py
class Coche:
    def __init__(self, nombre, velocidad_maxima, aceleracion):
        self.nombre = nombre
        self.velocidad_maxima = velocidad_maxima
        self.aceleracion = aceleracion
        self.posicion = 0.0
        self.velocidad = 0.0

    def mover(self, tiempo):
        # Actualizar velocidad con la aceleración y no superar la velocidad máxima
        self.velocidad += self.aceleracion * tiempo
        if self.velocidad > self.velocidad_maxima:
            self.velocidad = self.velocidad_maxima
        
        # Actualizar posición
        self.posicion += self.velocidad * tiempo

    def __str__(self):
        return f"{self.nombre} - Posición: {self.posicion:.2f}"

# carrera.py
class Carrera:
    def __init__(self):
        self.coches = []

    def agregar_coche(self, coche):
        self.coches.append(coche)

    def iniciar_carrera(self, duracion, intervalo):
        tiempo_actual = 0
        while tiempo_actual < duracion:
            print(f"Tiempo: {tiempo_actual:.2f}")
            for coche in self.coches:
                coche.mover(intervalo)
                print(coche)
            print()
            tiempo_actual += intervalo
        
        # Mostrar resultados finales
        print("Resultados finales:")
        for coche in self.coches:
            print(coche)
        
        # Determinar el ganador
        ganador = max(self.coches, key=lambda c: c.posicion)
        print(f"Ganador: {ganador.nombre}")

# main.py
if __name__ == "__main__":
    from coche import Coche
    from carrera import Carrera

    # Crear instancias de coches
    coche1 = Coche("Coche1", 120.0, 3.0)
    coche2 = Coche("Coche2", 100.0, 4.0)
    coche3 = Coche("Coche3", 110.0, 3.5)

    # Crear una carrera
    carrera = Carrera()
    carrera.agregar_coche(coche1)
    carrera.agregar_coche(coche2)
    carrera.agregar_coche(coche3)

    # Iniciar la carrera
    duracion = 10.0  # Duración total de la carrera en segundos
    intervalo = 1.0  # Intervalo de tiempo en segundos para actualizar la posición de los coches
    carrera.iniciar_carrera(duracion, intervalo)
