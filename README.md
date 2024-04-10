# Ansible in Azure

Este README describe los pasos para instalar Docker en un contenedor utilizando Ansible y luego ejecutar el contenedor que contiene el juego de Mario bros.

# Primer Paso
Configurar la infraestructura para una Máquina Virtual en Azure con IP Pública y Acceso mediante SSH utilizando un nombre de usuario y contraseña.

# Segundo Paso
Clonar el Repositorio que contiene la configuración de Ansible, modificando la información del Host según corresponda y seleccionando un puerto al cual el servicio responderá.

# Tercer Paso
Ejecutar los siguientes comandos:

1. Para instalar Docker ejecute el playbook install_docker.yml que se encuentra en la carpeta de playbooks para llevar a cabo la instalación de Docker en el sistema. Asegúrese de tener Ansible instalado y configurado correctamente antes de continuar:

  ansible-playbook -i inventory/hosts.ini playbooks/install_docker.yml

![image](https://github.com/PaulaTrujillo27/vm_ansible_azure/assets/71205932/e0bf1a2e-c60f-4cca-bcba-872c0b2f445e)


2. Como siguiente paso, es necesario ejecutar el contenedor, el cual también se encuentra ubicado en la carpeta de playbooks.

  ansible-playbook -i inventory/hosts.ini playbooks/run_container.yml

![image](https://github.com/PaulaTrujillo27/vm_ansible_azure/assets/71205932/2a6f920a-9700-4ce9-9c6f-6c81910918ce)


3. Luego, es necesario configurar una regla que permita realizar un reenvío de puerto para elegir el contenedor desde el cual se ejecutará. Para establecer esta regla, se debe acceder a las configuraciones de la máquina virtual desplegada en Azure. Diríjase al apartado de configuración de red y cree una lista de control de acceso (ACL) para el puerto de entrada que en este caso es el: 8090.

   *El reenvío de puerto (port forward) implica que el tráfico se direcciona desde el puerto 8090 del anfitrión hacia el puerto 8080 dentro del contenedor (se puede seleccionar el puerto desde el     playbook/run_container)*

![image](https://github.com/PaulaTrujillo27/vm_ansible_azure/assets/71205932/5a09a457-8de4-4d17-9d73-d331beca0cbd)

![image](https://github.com/PaulaTrujillo27/vm_ansible_azure/assets/71205932/5916edfe-90e4-49b9-ae23-fc0f236bf3d4)

4. Finalmente, se introduce en el navegador la dirección IP proporcionada por tu máquina virtual desplegada en Azure (IP Pública) junto con el puerto seleccionado. ¡Y así quedará listo para disfrutar!

![image](https://github.com/PaulaTrujillo27/vm_ansible_azure/assets/71205932/b1acf15c-7f3d-46cc-bce4-ee01f9ca161e)




