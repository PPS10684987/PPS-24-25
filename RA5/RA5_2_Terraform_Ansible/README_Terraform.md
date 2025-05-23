# Provisionamiento de una Máquina Virtual Ubuntu 24.04 en VirtualBox usando Terraform

Esta práctica muestra cómo utilizar Terraform para crear una máquina virtual de Ubuntu 24.04 en VirtualBox.

## Requisitos

Antes de comenzar, nos aseguraremos de tener instalado lo siguiente:

- VirtualBox
- Terraform
- Un archivo `.vdi` o `ova` válida de VirtualBox.

## Instalación del Provider VirtualBox para Terraform

Terraform no tiene un proveedor oficial de VirtualBox en su registro, por lo tanto utilizaremos el provider terra-form-provider-virtualbox. El repositorio terra-farm/terraform-provider-virtualbox es un proveedor no oficial de Terraform que permite interactuar con VirtualBox usando archivos .vdi para crear, configurar y administrar máquinas virtuales desde código.

1. Clonamos el repositorio oficial del provider:

    ```bash
    git clone https://github.com/terra-farm/terraform-provider-virtualbox.git
    ```
![captura](images_terraform/Captura19.PNG)

2. Creamos un directorio para Terraform y los archivos necesarios para la creación de la MV en terraform (main.tf):

    ```bash
    mkdir terraform-virtualbox
    nano main.tf
    ```

![captura](images_terraform/Captura1.PNG)

A continuación, dentro del archivo main.tf añadimos la definición de la máquina virtual a provisionar. Este archivo incluye el nombre de la VM, la cantidad de CPU, memoria, el adaptador de red y la ruta al archivo (image) `.vdi` u `ova`.
Además, deberemos especificar el provider que hemos clonado.

![captura](images_terraform/Captura14.PNG)

3. Actualización e Inicio de Terraform:

Para implementar correctamente el provider deberemos ejecutar el init de Terraform añadiendo el parametro "-upgrade". Así, lograremos installar el provider y se iniciara correctamente.

    ```bash
       terraform init -upgrade
    ```
![captura](images_terraform/Captura13.PNG)

## Ejecución del main.tf en Terraform

Al crear el archivo `main.tf` con la definición de la máquina virtual a provisionar e iniciar Terraform correctamente, ya podremos aplicar la configuración de la MV. Para ello, ejecutaremos "terraform apply" Terraform mostrará un resumen de los cambios que realizará. Escribimos yes para confirmar y proceder con la creación de la máquina virtual.
Finalmente, al finalizar la ejecución del terraform, nos dirigiremos a virtualbox y podremos observar que efectivamente se ha creado la MV en virtualbox mediante Terraform. Aunque tiene algún que otro error de creación, ya que me ha creado la MV pero sin ningún adaptador de red y tampoco con ningún disco. Este problema, no lo he conseguido solucionar.

![captura](images_terraform/Captura15.PNG)
![captura](images_terraform/Captura20.PNG)

