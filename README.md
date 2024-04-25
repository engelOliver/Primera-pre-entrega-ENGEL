# Primera-pre-entrega-ENGEL
                                         #CONSIGNA#
# El formato de registro es: Nombre de usuario y Contraseña.
# Utilizar una función para almacenar la información y otra función para mostrar la información.
# Utilizar un diccionario para almacenar dicha información, con el par usuario-contraseña (clave-valor).
# Utilizar otra función para el login de usuarios, comprobando que la contraseña coincida con el usuario.


Base_de_datos = {}

# La funcion que esta debajo se encarga de tomar los valores indicados por el usuario y guardarlos en el diccionario
# simulando su usuario y contraseña elegidos.
def register_user():
    new_user = input("Indique un nombre de usuario: ")
    print ("La contraseña debe tener al menos 10 caracteres y tambien contener al menos una mayuscula y un caracter especial")
    password = input("Indique una contraseña: ")
    Base_de_datos[new_user] = password
    print("Excelente! Te has registrado con exito.")

# Esta es la funcion solicitada para poder ver los par clave-valor
# o mas bien llamados key-value de nuestro diccionario que simula nuestra base de datos. 
# Es simple, simplemente cuando la llamamos desde el menu nos arroja los par clave-valor de nuestro diccionario

def see_Base_de_datos():
      print(Base_de_datos)

# Esta funcion se encarga del inicio de sesion del usuario chequeando con el bucle while si los datos dentro del diccionario
# existen y si coinciden las claves con sus respectivos valores.
# Tambien cuenta con un contador para determinarle al usuario que tiene 3 intentos para poder colocar sus datos correctamentte
# y asi ingresar a su cuenta registrada
def login(new_user, password):
  intentos = 1
  while (not new_user in Base_de_datos):
    if(intentos < 3):
      print("Usuario o contraseñaa incorrectos, por favor ingreselos de nuevo: ")
      new_user = input("Ingrese su nombre de usuario: ")
      password = input("Ingrese su contraseña: ")
      intentos += 1
    else:
      return False
  else:
    if Base_de_datos[new_user] != password:
      print("Usuario o contraseña incorrectos, por favor ingreselos de nuevo: ")
      new_user = input("Ingrese su nombre de usuario: ")
      password = input("Ingrese su contrasenia: ")
      intentos += 1
    else:
      return True

#Debajo esta el menu donde el usuario puede navegar en la pagina web/aplicacion y elgir que desea realizar#
def menu():
  print("¡Bienvenido/a!")
  option = 0
  while(option != 4):
    option = int(input("Coloque 1 para registrarse.\nColoque 2 para ver la base de datos.\nColoque 3 iniciar sesion.\nColoque 4 para salir del inicio de sesion.\nIndique una de las siguientes opciones con un numero: "))
    if(option == 1):
      register_user() # Aqui invocamos a la funcion propiamente vista en esta linea
    elif(option == 2):
      see_Base_de_datos() #Aqui invocamos a la funcion propiamente vista en esta linea
    elif(option == 3):
      new_user = input("Ingrese su nombre de usuario: ")
      password = input("Ingrese su contrasenia: ")
      successful_login = login(new_user, password)
      if not successful_login:
        print ("""Usuario y contraseña incorrectos.\n3
        Debido a que los 3 intentos de iniciar sesion han sido fallidos, vuelve a intetarlo nuevamente dentro de 30 minutos.""")
        break
      else : #Esta opcion simplente se cumple si no se agotaron los intentos y el usuario coloca sus datos correctamente#
        print("Iniciando sesion...")
        break
    elif(option == 4): #Esta opcion simplemente sale del bucle arrojando el mensaje que se puede ver dentro del siguiente print#
      print("Cerrando aplicacion")
      break

# Aca invocamos a nuestra funcion menu, que seria nuestra funcion maestra por asi decirlo
# y asi poder interactuar con todo el codigo

menu() 

