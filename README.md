<!DOCTYPE html>
<html lang="es">
<cabeza>
    <meta charset="UTF-8" />
    <meta name="viewport" content="ancho=ancho-del-dispositivo, escala-inicial=1" />
    <title>Registro de Consultas Médicas</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <estilo>
        cuerpo {
            familia de fuentes: Arial, sans-serif;
            margen: 30px;
            color de fondo: #35ecbe;
        }
        h1 {
            color: #2c3e50;
        }
        forma {
            fondo: blanco;
            relleno: 20px;
            radio del borde: 8px;
            ancho máximo: 500px;
            caja-sombra: 0 0 10px rgba(0,0,0,0.1);
        }
        etiqueta {
            pantalla: bloque;
            margen superior: 15px;
            peso de fuente: negrita;
        }
        entrada, seleccionar {
            ancho: 100%;
            relleno: 8px;
            margen superior: 5px;
            tamaño de caja: caja de borde;
        }
        botón {
            margen superior: 20px;
            relleno: 10px;
            color de fondo: #0000FF;
            color: blanco;
            borde: ninguno;
            ancho: 100%;
            tamaño de fuente: 16px;
            cursor: puntero;
            radio del borde: 4px;
        }
        botón:hover {
            color de fondo: #219150;
        }
        .notificación {
            margen superior: 15px;
            relleno: 10px;
            color de fondo: #dff0d8;
            color: #3c763d;
            radio del borde: 4px;
            pantalla: ninguna;
        }
    </estilo>
</cabeza>
<cuerpo>
    <h1>Registro de Consulta Médica</h1>
    <form id="ConsultaForm">
        <label for="turno">Turno</label>
        <select id="turno" requerido>
            <option value="">Seleccione un turno</option>
            <option value="Mañana">Mañana</option>
            <option value="vespertino">vespertino</option>
            <option value="Noche">Noche</option>
        </seleccionar>

        <label for="hora">Hora</label>
        <input type="time" id="hora" requerido />

        <label for="medico">Médico</label>
        <select id="medico" requerido>
            <option value="">Seleccione un médico</option>
            <option value="Dr. Juan Pérez">Dr. Juan Pérez</opción>
            <option value="Dra. María Gómez">Dra. María Gómez</opción>
            <option value="Dr. Carlos Ruiz">Dr. Carlos Ruiz</option>
            <option value="Dr. Luis Gotera">Dr. Luis Gotera</opción>
        </seleccionar>

        <label for="notificacion">Notificación o Confirmación</label>
        <seleccione id="notificación" requerida>
            <option value="">Seleccione una opción</option>
            <option value="Confirmado">Confirmado</option>
            <option value="Pendiente">Pendiente</option>
            <option value="Cancelado">Cancelado</option>
        </seleccionar>

        <button type="submit">Registrar Consulta y Generar Informe PDF</button>
    </form>

    <div class="notificación" id="notificación"></div>

    <guión>
        const { jsPDF } = ventana.jspdf;

        document.getElementById('consultaForm').addEventListener('enviar', función(e) {
            e.preventDefault();

            // Obtener valores del formulario
            const turno = document.getElementById('turno').value;
            const hora = document.getElementById('hora').value;
            const medico = document.getElementById('medico').value;
            notificación const = document.getElementById('notificación').value;

            // Validar (ya está requerido, pero por seguridad)
            if (!turno || !hora || !medico || !notificacion) {
                alert('Por favor, completa todos los campos.');
                devolver;
            }

            // Crear documento PDF
            constante doc = nuevo jsPDF();

            doc.setFontSize(18);
            doc.text('Informe de Consulta Médica', 20, 20);

            doc.setFontSize(12);
            doc.text(`Turno: ${turno}`, 20, 40);
            doc.text(`Hora: ${hora}`, 20, 50);
            doc.text(`Médico: ${medico}`, 20, 60);
            doc.text(`Estado de Notificación: ${notificación}`, 20, 70);

            const fechaActual = new Date().toLocaleString();
            doc.text(`Fecha de Registro: ${fechaActual}`, 20, 80);

            

            
            const fileName = `Informe_Consulta_${medico.replace(/\s+/g, '_')}_${fechaActual.replace(/[/,: ]/g, '_')}.pdf`;
            doc.save(nombreArchivo);

            
            const notificationDiv = document.getElementById('notificación');
            notificaciónDiv.style.display = 'bloque';
            notificationDiv.textContent = 'Consulta registrada y PDF generada correctamente.';

           

            
            esto.reset();
        });
    </script>
</cuerpo>
</html>
