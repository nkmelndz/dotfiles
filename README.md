# Dotfiles y configuración

## Configuración de i3wm

1. **Instalar i3wm**  
   ```bash
   sudo apt update
   sudo apt install i3
   ```

2. **Copiar archivos de configuración**  
   Copia el archivo `i3/config` a tu carpeta de configuración:
   ```bash
   mkdir -p ~/.config/i3
   cp i3/config ~/.config/i3/config
   ```

3. **Instalar utilidades recomendadas**  
   ```bash
   sudo apt install i3status i3lock dmenu
   ```

---

## Configuración de i3status

1. **Copiar archivo de configuración**  
   Copia el archivo de configuración a la ruta del sistema:
   ```bash
   sudo cp i3status.conf /etc/i3/i3status.conf
   ```

2. **Editar el archivo si es necesario**  
   Puedes personalizar los módulos y la información que muestra editando `/etc/i3/i3status.conf`.

---

## Activar configuración de control manual de ventilador (ThinkPad)

1. **Habilitar control manual**  
   Agrega la opción al archivo de configuración del módulo:
   ```bash
   echo 'options thinkpad_acpi fan_control=1' | sudo tee /etc/modprobe.d/thinkpad_acpi.conf
   ```

2. **Recargar el módulo**  
   ```bash
   sudo modprobe -r thinkpad_acpi
   sudo modprobe thinkpad_acpi
   ```

---

## Servicio systemd para control de ventilador

(Mejor opción si quieres que se ejecute al arrancar el sistema)

1. **Crear el servicio**  
   ```bash
   sudo cp fan-control.service /etc/systemd/system/fan-control.service
   ```

2. **Habilitar y arrancar el servicio**  
   ```bash
   sudo systemctl enable fan-control.service
   sudo systemctl start fan-control.service
   ```