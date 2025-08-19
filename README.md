<?php

try {
    $pdo = new PDO("mysql:host=localhost;dbname=meubanco", "usuario", "senha");
    // Configura o PDO para lançar exceções em caso de erros
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Conexão bem-sucedida!";
} catch (PDOException $e) {
    echo "Erro ao conectar ao banco de dados: " . $e->getMessage();
}

isset ($_POST['register-form']){
    $name = $_POST['name'];
    $email = $_POST['email'];
    $password = $_POST['password'];
    $conf_pass = $_POST['conf_pass'];
    $birth = $_POST['birth'];
    $role = $_POST['role'];
}

// validações

if($password != $conf_pass){
    // erro
} else {
    try {
        // deu certo
        $sql = "INSERT INTO usuarios (nome, email, idade) VALUES (:nome, :email, :idade)";
        $stmt = $pdo->prepare($sql);

        // Bind dos parâmetros
        $stmt->bindParam(':nome', $nome);
        $stmt->bindParam(':email', $email);
        $stmt->bindParam(':idade', $idade);
        
        echo "Novo usuário inserido com sucesso!";
    } catch (PDOException $e) {
        echo "Erro ao inserir: " . $e->getMessage();
    }
}

?>
