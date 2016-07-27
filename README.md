PHP ITAUCRIPTO Itau Bankline
==============

Vers�o em PHP da classe Itaucripto, originalmente escrita em Java baseado em gabrielrcouto/php-itaucripto.

O nome dos m�todos foi mantido seguindo o padr�o Java, apenas para evitar confus�es.

Nessa classe apenas implementamos o uso pelo Composer e uso de excess�es em caso de erro nos dados.

Como a classe em Java foi descompilada, alguns nomes se tornaram nomes gen�ricos (ex: $paramString1, $paramString2).

Instala��o
==============
```php
composer require dilneiss/itaubankline
```

Como Usar
==============

Ap�s o cliente preencher os dados, criptografe eles utilizando o seguinte c�digo:

```php
  $cripto = new ItauCripto();
  
  //Coloque o c�digo da empresa em MAI�SCULO
  $codEmp = "J1234567890123456789012345";
  //Coloque a chave de criptografia em MAI�SCULO
  $chave = "ABCD123456ABCD12";
  
  //Preencha as vari�veis abaixo com os dados do cliente e da cobran�a
  //Abaixo � s� um exemplo!
  $pedido = "1234";
  $valor = "150,00";
  $observacao = "";
  $nomeSacado = "Jos� Pereira";
  $codigoInscricao = "";
  $numeroInscricao = "";
  $enderecoSacado = "";
  $bairroSacado = "";
  $cepSacado = "";
  $cidadeSacado = "";
  $estadoSacado = "";
  $dataVencimento = "";
  $urlRetorna = "";
  $obsAd1 = "";
  $obsAd2 = "";
  $obsAd3 = "";
  
	try {
	  $dados_criptografados = $cripto->geraDados($codEmp,$pedido,$valor,$observacao,$chave,$nomeSacado,
	      $codigoInscricao,$numeroInscricao,$enderecoSacado,$bairroSacado,$cepSacado,$cidadeSacado,$estadoSacado,
	      $dataVencimento,$urlRetorna,$obsAd1,$obsAd2,$obsAd3);
	} catch (Exception $e) {
		exit($e->getMessage());
	}
  
```

Caso queira redirecionar o cliente para a tela do Itau Bankline e selecionar a op��o de pagamento desejada, utilize a url abaixo.
```php
	$url = "https://shopline.itau.com.br/shopline/shopline.aspx?DC=$dados_criptografados";
```

Para gerar o boleto diretamente sem acessar a tela do Itau Bankline, utilize a url abaixo.
```php
	$url = "https://shopline.itau.com.br/shopline/Itaubloqueto.asp?DC=$dados_criptografados";
```


Campos
==============

```php
  $pedido // Identifica��o do pedido - m�ximo de 8 d�gitos (12345678) - Obrigat�rio  
  $valor // Valor do pedido - m�ximo de 8 d�gitos + v�rgula + 2 d�gitos - 99999999,99 - Obrigat�rio  
  $observacao // Observa��es - m�ximo de 40 caracteres  
  $nomeSacado // Nome do sacado - m�ximo de 30 caracteres  
  $codigoInscricao // C�digo de Inscri��o: 01->CPF, 02->CNPJ  
  $numeroInscricao // N�mero de Inscri��o: CPF ou CNPJ - at� 14 caracteres  
  $enderecoSacado // Endereco do Sacado - m�ximo de 40 caracteres  
  $bairroSacado // Bairro do Sacado - m�ximo de 15 caracteres  
  $cepSacado // Cep do Sacado - m�ximo de 8 d�gitos  
  $cidadeSacado // Cidade do sacado - m�ximo 15 caracteres  
  $estadoSacado // Estado do Sacado - 2 caracteres  
  $dataVencimento // Vencimento do t�tulo - 8 d�gitos - ddmmaaaa  
  $urlRetorna // URL do retorno - m�ximo de 60 caracteres  
  $obsAdicional1 // ObsAdicional1 - m�ximo de 60 caracteres  
  $obsAdicional2 // ObsAdicional2 - m�ximo de 60 caracteres  
  $obsAdicional3 // ObsAdicional3 - m�ximo de 60 caracteres
```

Author
==============

[@dilneiss88](http://twitter.com/dilneiss88)

Licen�a
==============

[MIT License](http://zenorocha.mit-license.org/)
