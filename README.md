# examen_extraordinaria_2023_2024_marta_nieto_romero
Ejercicio 3
class Tarea:
    def __init__(self, titulo, descripcion=''):
        self.titulo = titulo
        self.descripcion = descripcion

    def __str__(self):
        return f"Título: {self.titulo}, Descripción: {self.descripcion}"


class GestorDeTareas:
    def __init__(self):
        self.tareas = []

    def agregar_tarea(self, titulo, descripcion=''):
        nueva_tarea = Tarea(titulo, descripcion)
        self.tareas.append(nueva_tarea)
        print(f"Tarea '{titulo}' agregada.\n")

    def eliminar_tarea(self, titulo):
        for tarea in self.tareas:
            if tarea.titulo == titulo:
                self.tareas.remove(tarea)
                print(f"Tarea '{titulo}' eliminada.\n")
                return
        print(f"No se encontró una tarea con el título '{titulo}'.\n")

    def mostrar_tareas(self):
        if not self.tareas:
            print("No hay tareas en la lista.\n")
        else:
            print("Lista de tareas:")
            for tarea in self.tareas:
                print(tarea)
            print()


def menu():
    gestor = GestorDeTareas()

    while True:
        print("Menú de gestión de tareas:")
        print("1. Agregar tarea")
        print("2. Eliminar tarea")
        print("3. Mostrar tareas")
        print("4. Salir")
        opcion = input("Selecciona una opción: ")

        if opcion == '1':
            titulo = input("Título de la tarea: ")
            descripcion = input("Descripción de la tarea (opcional): ")
            gestor.agregar_tarea(titulo, descripcion)
        elif opcion == '2':
            titulo = input("Título de la tarea a eliminar: ")
            gestor.eliminar_tarea(titulo)
        elif opcion == '3':
            gestor.mostrar_tareas()
        elif opcion == '4':
            print("Saliendo del gestor de tareas.")
            break
        else:
            print("Opción no válida, por favor selecciona una opción del 1 al 4.\n")


if __name__ == "__main__":
    menu()

