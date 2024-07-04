# examen_extraordinaria_2023_2024_marta_nieto_romero
Ejercicio 1
def es_primo(n):
    """Función que verifica si un número es primo."""
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

def factores_primos(n):
    """Función que devuelve una lista de factores primos de n."""
    factores = []
    divisor = 2
    while n > 1:
        while n % divisor == 0:
            factores.append(divisor)
            n //= divisor
        divisor += 1
        if divisor * divisor > n:
            if n > 1:
                factores.append(n)
                break
    return factores

def solicitar_numero():
    """Función que solicita un número entero mayor que 1 al usuario."""
    while True:
        try:
            numero = int(input("Ingrese un número entero mayor que 1: "))
            if numero > 1:
                return numero
            else:
                print("El número debe ser mayor que 1. Inténtelo de nuevo.")
        except ValueError:
            print("Entrada no válida. Por favor, ingrese un número entero.")

def main():
    numero = solicitar_numero()
    factores = factores_primos(numero)
    print(f"Factores primos de {numero}: {factores}")

if __name__ == "__main__":
    main()
