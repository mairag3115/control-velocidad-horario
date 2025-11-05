# control-velocidad-horario
"Sistema de control de velocidad que aplica diferentes límites (km/h) según la hora del día, utilizando lógica condicional (if/elif). Proyecto basado en un diagrama de flujo."
# main.py
# Este archivo contiene la lógica para determinar el límite de velocidad según la hora.

def determinar_velocidad(hora):
"""
    Función que determina la velocidad máxima permitida (en km/h) 
    basada en la hora del día (formato 24 horas, entero).
    
    La lógica se basa en el diagrama de flujo proporcionado.

    Args:
        hora (int): La hora del día (0 a 23).

        Returns:
        str: Un mensaje indicando la velocidad máxima permitida o un error.
    """
    # 1. Validación de la entrada
    if not isinstance(hora, int) or hora < 0 or hora > 23:
        return "Error: La hora debe ser un número entero entre 0 y 23."
        velocidad = 0 # Inicializamos la variable de velocidad

        # 2. Aplicación de la lógica del diagrama (Sentencias if/elif)
    
    # Rango 1: 00:01 a 08:00 (Velocidad: 45 km/h)
    if 0 < hora <= 8:
        velocidad = 45
        
    # Rango 2: 08:01 a 12:00 (Velocidad: 30 km/h)
    elif 8 < hora <= 12:
        velocidad = 30
        # Rango 3: 12:01 a 18:00 (Velocidad: 40 km/h)
    elif 12 < hora <= 18:
        velocidad = 40
        
    # Rango 4: 18:01 a 22:00 (Velocidad: 25 km/h)
    elif 18 < hora <= 22:
        velocidad = 25
        
    # Rango 5: 22:01 a 00:00 (Velocidad: 45 km/h)
    # Cubre las 23:00 y las 00:00 (representado como 0 en programación).
    elif 22 < hora <= 23 or hora == 0: 
        velocidad = 45
        
    else:
        # Esta es una condición de seguridad, poco probable si la validación inicial es correcta.
        return "Error: Lógica de rango no cubierta."

    return f"La velocidad máxima permitida a las {hora:02d}:00 es de {velocidad} km/h."

# --- Bloque de Ejecución Principal (Pruebas) ---

if __name__ == "__main__":
    print("--- Sistema de Control de Velocidad por Horario ---")
    
    # Ejecuta la función con horas de prueba:
    print(f"Hora 8:00: {determinar_velocidad(8)}")
    print(f"Hora 10:00: {determinar_velocidad(10)}")
    print(f"Hora 15:00: {determinar_velocidad(15)}")
    print(f"Hora 20:00: {determinar_velocidad(20)}")
    print(f"Hora 0:00: {determinar_velocidad(0)}")
