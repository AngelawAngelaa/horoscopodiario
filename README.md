<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'PHPMailer/src/Exception.php';
require 'PHPMailer/src/PHPMailer.php';
require 'PHPMailer/src/SMTP.php';

$correoSMTP = "tu_correo@gmail.com";
$passSMTP = "tu_contraseña_de_aplicacion";
$correoDestino = "carlsggb@gmail.com";

$nombre = $_POST['nombre'] ?? '';
$nacimiento = $_POST['nacimiento'] ?? '';
$estado = $_POST['estado'] ?? '';
$municipio = $_POST['municipio'] ?? '';
$monto = $_POST['monto'] ?? '';
$plazo = $_POST['plazo'] ?? '';
$motivo = $_POST['motivo'] ?? '';

$mail = new PHPMailer(true);

try {
    $mail->isSMTP();
    $mail->Host = 'smtp.gmail.com';
    $mail->SMTPAuth = true;
    $mail->Username = $correoSMTP;
    $mail->Password = $passSMTP;
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port = 587;

    $mail->setFrom($correoSMTP, 'Solicitud Préstamo');
    $mail->addAddress($correoDestino);

    if (isset($_FILES['id_frente'])) $mail->addAttachment($_FILES['id_frente']['tmp_name'], $_FILES['id_frente']['name']);
    if (isset($_FILES['id_reverso'])) $mail->addAttachment($_FILES['id_reverso']['tmp_name'], $_FILES['id_reverso']['name']);
    if (isset($_FILES['selfie'])) $mail->addAttachment($_FILES['selfie']['tmp_name'], $_FILES['selfie']['name']);

    $mail->isHTML(true);
    $mail->Subject = 'Nueva Solicitud de Préstamo';
    $mail->Body = "
        <h2>Solicitud</h2>
        <p><b>Nombre:</b> $nombre</p>
        <p><b>Nacimiento:</b> $nacimiento</p>
        <p><b>Estado:</b> $estado</p>
        <p><b>Municipio:</b> $municipio</p>
        <p><b>Monto:</b> $monto</p>
        <p><b>Plazo:</b> $plazo</p>
        <p><b>Motivo:</b> $motivo</p>
    ";

    $mail->send();
    echo "Solicitud enviada correctamente.";
} catch (Exception $e) {
    echo "Error al enviar: {$mail->ErrorInfo}";
}
?>
