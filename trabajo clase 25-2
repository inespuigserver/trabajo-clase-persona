import math
import random

tamaño_matriz = 4  # elegimos tamaño 4 porque somos 4 personas en el grupo

class Persona:
    def __init__(self, nombre, año_nacimiento, x, y):
        self.nombre = nombre
        self.año_nacimiento = año_nacimiento
        self.x = x
        self.y = y
        self.contador_movimientos = 0

    def mover_aleatorio(self):
        despx = random.randint(-1, 1)
        despy = random.randint(-1, 1)

        # Evitar salir de la matriz
        nuevo_x = self.x + despx
        nuevo_y = self.y + despy
        if 0 <= nuevo_x < tamaño_matriz:
            self.x = nuevo_x
        if 0 <= nuevo_y < tamaño_matriz:
            self.y = nuevo_y

        self.contador_movimientos += 1
        return f"{self.nombre} se movió a ({self.x}, {self.y})"

    def hablar(self, otra):
        mensajes = [
            f"{self.nombre} y {otra.nombre} discuten quién paga la comida ",
            f"{self.nombre} invita a {otra.nombre} a la playa ",
            f"{self.nombre} le cuenta un chisme a {otra.nombre} ",
            f"{self.nombre} propone hacer un viaje con {otra.nombre} ",
            f"{self.nombre} y {otra.nombre} hablan del examen "
        ]
        print(random.choice(mensajes))

    def pelear(self, otra):
        peleas = [
            f" {self.nombre} y {otra.nombre} se pelean por el último café ",
            f" {self.nombre} empuja a {otra.nombre} sin querer ",
            f" {self.nombre} y {otra.nombre} discuten por llegar tarde "
        ]
        print(random.choice(peleas))

class Espacio:
    def __init__(self, nombre):
        self.nombre = nombre
        self.personas = []
        self.registro_movimientos = []

    def agregar_persona(self, persona):
        self.personas.append(persona)

    def listar_personas(self):
        print(f"Personas en {self.nombre}")
        for persona in self.personas:
            print(f" - {persona.nombre} en ({persona.x}, {persona.y})")

    def mover_personas(self):
        for persona in self.personas:
            mov = persona.mover_aleatorio()
            print(mov)
            self.registro_movimientos.append(mov)

    def comprobar_interacciones(self):
        for i in range(len(self.personas)):
            for j in range(i + 1, len(self.personas)):
                p1 = self.personas[i]
                p2 = self.personas[j]

                dist = calcular_distancia(p1, p2)

                if misma_posicion(p1, p2):
                    p1.pelear(p2)
                elif dist == 1:
                    p1.hablar(p2)

    def mostrar_matriz(self):
        matriz = [["." for _ in range(tamaño_matriz)] for _ in range(tamaño_matriz)]
        for p in self.personas:
            inicial = p.nombre[0].upper()
            matriz[p.y][p.x] = inicial
        for fila in matriz:
            print(" ".join(fila))

def calcular_distancia(persona1, persona2):
    return math.sqrt((persona1.x - persona2.x) ** 2 + (persona1.y - persona2.y) ** 2)

def misma_posicion(persona1, persona2):
    return persona1.x == persona2.x and persona1.y == persona2.y

def simular_tiempo(espacio, pasos=20):
    print("SIMULACIÓN")
    for paso in range(1, pasos + 1):
        print(f"PASO {paso}")
        espacio.mover_personas()
        espacio.mostrar_matriz()
        espacio.comprobar_interacciones()

# creación del espacio y de las personas
aula = Espacio("Aula 1")
esther = Persona("Esther", 2007, 0, 0)
alejandra = Persona("Alejandra", 2007, 3, 0)
ines = Persona("Inés", 2007, 0, 3)
maia = Persona("Maia", 2004, 3, 3)

aula.agregar_persona(esther)
aula.agregar_persona(alejandra)
aula.agregar_persona(ines)
aula.agregar_persona(maia)

# Estado inicial
aula.listar_personas()

# Simulación
simular_tiempo(aula, 20)

# Resultados finales
print("RESULTADOS FINALES")
for p in aula.personas:
    print(f"{p.nombre} hizo {p.contador_movimientos} movimientos y terminó en ({p.x}, {p.y})")