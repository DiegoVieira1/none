# none
projeto formulário de cadastro
  <html>
    <head>
        <!-- Compiled and minified CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css">

    <!-- Compiled and minified JavaScript -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js"></script>
            
      <!--Import Google Icon Font-->
      <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
      <!--Import materialize.css-->
      <link type="text/css" rel="stylesheet" href="css/materialize.min.css"  media="screen,projection"/>

      <!--Let browser know website is optimized for mobile-->
      <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    </head>

    <body>
                        <!-- barra superior ---->
      <nav>
        <div class="nav-wrapper">
          <a href="#" class="brand-logo right"><li></li></a>
          <ul id="nav-mobile" class="left hide-on-med-and-down">
          </ul>
        </div>
      </nav>
		<!--JavaScript at end of body for optimized loading-->
		<script type="text/javascript" src="js/materialize.min.js"></script>
    </body>
    <div class="row">
      <form class="col s12">
        <div class="row">
          <div class="input-field col s6">
                          <!---- linha de nome ---->
            <input placeholder="Nome Completo" id="Nome" type="text" class="validate">
            <label for="Nome"></label>
                           <!------ cauculo de idade ------>
	<script> 
		function calcularIdade() {
			var dataNascimento = document.getElementById("dataNascimento").value;
			var dataAtual = new Date();
			var dataNascimentoFormatada = new Date(dataNascimento);
      
			var diferencaAnos = dataAtual.getFullYear() - dataNascimentoFormatada.getFullYear();
      
			document.getElementById("resultado").innerHTML = "Idade: " + diferencaAnos + " anos";
    }
		</script>
    <br><br>
		<body>
            <!--- data de nascimento --->
			<label for="dataNascimento"></label>
			<input type="date" id="dataNascimento" name="dataNascimento">
		
      <a class="waves-effect waves-light btn"onclick="calcularIdade()">ok</a>
  
			<div id="resultado"></div>
          <!-- seletor de Genero-->
		      Genero
		<br><form action="#">
      <p>
        <label>
          <input name="group1" type="radio" checked />
          <span>Masculino</span>
        </label>
      </p>
      <p>
        <label>
          <input name="group1" type="radio" />
          <span>Feminino</span>
        </label>
      </p>
            <!-- cep -->
		<label for="cep"></label>
  <input type="text" id="cep" placeholder="Digite o CEP">
  <a class="waves-effect waves-light btn"onclick="buscarEndereco()">Buscar</a>
  <p id="endereco"></p>
  <p id="logradouro"></p>
  <p id="bairro"></p>
  <p id="localidade"></p>
  <p id="uf"></p>
            <!-- Busca de cep  pelo viacep -->
  <script>
    function buscarEndereco() {
      var cep = document.getElementById("cep").value;
      var xhr = new XMLHttpRequest();
      
      xhr.open("GET", "https://viacep.com.br/ws/" + cep + "/json/", true);
      
      xhr.onreadystatechange = function() {
        if (xhr.readyState == 4 && xhr.status == 200) {
          var endereco = JSON.parse(xhr.responseText);
          
          if (endereco.erro) {
            document.getElementById("endereco").innerHTML = "CEP não encontrado.";
            document.getElementById("logradouro").innerHTML = "";
            document.getElementById("bairro").innerHTML = "";
            document.getElementById("localidade").innerHTML = "";
            document.getElementById("uf").innerHTML = "";
          } else {
            document.getElementById("endereco").innerHTML = "Endereço:";
            document.getElementById("logradouro").innerHTML = "Logradouro: " + endereco.logradouro;
            document.getElementById("bairro").innerHTML = "Bairro: " + endereco.bairro;
            document.getElementById("localidade").innerHTML = "Cidade: " + endereco.localidade;
            document.getElementById("uf").innerHTML = "UF: " + endereco.uf;
          }
        }
      };
      
      xhr.send();
    }
  </script>
		
	
	
	
  </html>
