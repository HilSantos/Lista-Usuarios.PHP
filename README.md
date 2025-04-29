# Lista-Usuarios.PHP
Criação de um novo projeto no ti35.

-- Crie um db_proj35 e depois uma tabela --

CREATE DATABASE db_proj35

-- Clicar em Executar --

CREATE TABLE tb_usuarios(
    id_usuario          INT PRIMARY KEY AUTO_INCREMENT,
    nome_usuario        VARCHAR(50),
    apelido_usuario     VARCHAR(15),
    cpf_usuario         VARCHAR(14),
    email_usuario       VARCHAR(40) UNIQUE,
    cep_usuario         VARCHAR(9),
    rua_usuario         VARCHAR(50),
    numero_rua_usuario  VARCHAR(5),
    bairro_usuario      VARCHAR(30),
    cidade_usuario      VARCHAR(30),
    uf_usuario          VARCHAR(2),
    nascimento_usuario  DATE,
    senha_usuario       VARCHAR(32),
    tempero_usuario	    VARCHAR(32),
    telefone_usuario    VARCHAR(11),
    recupera_usuario    VARCHAR(8),
    nivel_usuario       INT,
    dt_criacao_usuario  DATETIME);
    -----------------------------------------------------------------------------------------------------------------------------------
-- Crie uma nova pasta e uma Lista Usuarios --

<?php
$servidor = "localhost";
$banco = "db_proj35";
$db_user = "adminti35";
$db_senha = "789abc";
$link = mysqli_connect($servidor, $db_user, $db_senha, $banco);
$sql = "SELECT id_usuario, nome_usuario, cpf_usuario, email_usuario, telefone_usuario, nivel_usuario FROM tb_usuarios";
$result = mysqli_query($link, $sql);
?>

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista Usuarios</title>
</head>
<body>
    <h1>Lista Usuarios</h1>
    <br>
    <br>
    <table border = "1">
        <tr>
            <th>*****</th>
            <th>Nome</th>
            <th>Email</th>
            <th>Telefone</th>
            <th>CPF</th>
            <th>Nivel</th>
            <th>*****</th>
            <th>*****</th>
        </tr>
        <?php
        while($tbl = mysqli_fetch_array($result)){
        ?>
        <tr>
        <td></td>
        <td><?= $tbl[1] ?></td>
        <td><?= $tbl[3] ?></td>
        <td><?= $tbl[4] ?></td>
        <td><?= $tbl[2] ?></td>
        <td><?= $tbl[5] ?></td>
        <td></td>
        <td></td>
        </tr>
        <?php
        }
        ?>
    </table>
</body>
</html>
-------------------------------------------------------------------------------------------------------------------------------------

-- Peça ao ChatGPT para criar os inserts --

INSERT INTO tb_usuarios (
    nome_usuario, apelido_usuario, cpf_usuario, email_usuario, cep_usuario,
    rua_usuario, numero_rua_usuario, bairro_usuario, cidade_usuario, uf_usuario,
    nascimento_usuario, senha_usuario, tempero_usuario, telefone_usuario,
    recupera_usuario, nivel_usuario, dt_criacao_usuario
) VALUES
('Ana Paula da Silva', 'aninha', '123.456.789-00', 'ana.silva@email.com', '12345-678',
 'Rua das Flores', '123', 'Centro', 'São Paulo', 'SP',
 '1990-05-10', 'senha123hashed', 'sal123', '11999998888',
 'ana2024', 1, NOW()),

('Bruno Marques Souza', 'brunim', '987.654.321-00', 'bruno.souza@email.com', '87654-321',
 'Av. Paulista', '456', 'Bela Vista', 'São Paulo', 'SP',
 '1985-11-20', 'senha456hashed', 'sal456', '11988887777',
 'bru2024', 2, NOW()),

('Carla Regina Mota', 'carlita', '321.654.987-00', 'carla.mota@email.com', '65432-109',
 'Rua do Sol', '78', 'Jardim América', 'Rio de Janeiro', 'RJ',
 '1995-07-15', 'senha789hashed', 'sal789', '21977776666',
 'car2024', 1, NOW()),

('Diego Lima', 'diegão', '456.789.123-00', 'diego.lima@email.com', '54321-987',
 'Travessa dos Pássaros', '12A', 'Copacabana', 'Rio de Janeiro', 'RJ',
 '1992-03-22', 'senha321hashed', 'sal321', '21966665555',
 'die2024', 1, NOW()),

('Eduarda Ferreira', 'duda', '789.123.456-00', 'eduarda.ferreira@email.com', '43210-876',
 'Rua das Acácias', '900', 'Santa Cecília', 'Belo Horizonte', 'MG',
 '2000-12-01', 'senha654hashed', 'sal654', '31955554444',
 'edu2024', 2, NOW());

-- Atualize a pagina e faça o teste (explo: http://localhost/proj35/listausuarios.php) --
