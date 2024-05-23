the_diccionario = {}
pendiente_lista = []

import os

def clear_screen():
    os.system('cls' if os.name == 'nt' else 'clear')

def add_service(service_dict, service_id, name, price):
    if service_id == '' or name == '' or price == '':
        input('Debe completar toda la información requerida. Presione <ENTER> para continuar.')
    else:
        price = float(price)
        service_dict[service_id] = {'name': name, 'price': price}
        input(f'\nService "{name}" has been added successfully. Press <ENTER> to continue.')

def show_services(service_dict):
    if service_dict:
        print("\nCurrent services and prices:")
        for service_id, service_info in service_dict.items():
            print(f"{service_id}. {service_info['name']}: ${service_info['price']:.2f}")
    else:
        print("No services available.")
    input('\nPress <ENTER> to continue.')

def add_pending(pending_list, contact):
    pending_list.append(contact)
    input('\nDue to not meeting the requirements, the contact has been added to the pending list successfully. Press <ENTER> to continue.')

def main_menu():
    clear_screen()
    print('\n<<<<<<<<<MAIN MENU>>>>>>>>>>\n\n1. Add Service\n2. Show Services\n3. Exit')
    return input('-> ')

def selector(option):
    global the_diccionario
    global pendiente_lista
    if option == '1':
        clear_screen()
        service_id = input('Service ID: ')
        name = input('Service Name: ')
        price = input('Price: ')
        add_service(the_diccionario, service_id, name, price)
    elif option == '2':
        clear_screen()
        show_services(the_diccionario)
    elif option == '3':
        return False
    return True

running = True    
while running:
    running = selector(main_menu())
