
# Criar modulo

Instruções de como criar um modulo genérico. Modulos genéricos são todos os outros módulos que existem além do modulo system. A aplicação é composta do modulo System, referente a aplicação em si (O sistema). O system por sua vez é formado por vários módulos genéricos.  


## 1. Criar diretório

 <!-- Dentro da pasta modulos, crie a pasta do modulo e dentro dessa nova pasta crie os arquivos que vão compor o modulo, da seguinte forma: -->

 Dentro da pasta modulos crie uma pasta com o nome do novo modulo. Em seguida, dentro dessa nova pasta crie os arquivos seguindo a estrutura básica de um modulo, conforme imagem abaixo: 


![Arquitetura de um modulo](assets/arq_modulo.png)



Nos próximos passos iremos preencher os conteúdos dos arquivos criados, por enquanto podem ficar vazios. 



## 2. Estrutura e arquivos

Nesse próximo passo iremos entender cada arquivo que compõe a estrutura de um módulo.


###  Arquivo .modulo

O arquivo que possui a extensão ***".modulo"*** é o arquivo de acesso e configuração do nosso modulo. Esse arquivo disponibiliza a view e o controller do nosso modulo. Confira abaixo como deve ficar o conteúdo do arquivo, utilizando como exemplo um modulo chamado "produtos". 

``` dart  hl_lines="9 12 16-19 24-26" linenums="1"
import 'package:custom_app/custom_app/custom_app.imports.dart';
import 'package:custom_app/custom_app/web_app/web_app.imports.dart';
import 'package:flutter/material.dart';
import 'produtos.view.dart';

class Produtos implements WebAppModulo {
  
  @override
  String displayName = "Produtos";

  @override
  int idModulo = 1; 

  @override
  WebModuleView get view => WebModuleView.basic(
    widget: ProdutosView(
      displayName: displayName,  /// A view recebe o parametro 'displayName'
      modulo: this,  /// A view recebe o porametro 'modulo'
    ),
  );

  @override
  MenuPiece menuPiece = MenuPiece.apartButton(
    buttonTitle: "Produtos",   // Texto do botão
    menuPos: 1, // Posição do botão no menu 
    icon: Icons.person_outline,  // Icone do botão 
  );

}
```


### Arquivo .view

O arquivo que possui a extensão ***".view"*** será responsável pela parte visual do nosso modulo. É dentro desse arquivo que serão realizadas alterações para modificar a tela. Abaixo segue como deve ficar o código da camada 'view', ainda usando o nosso exemplo de um modulo chamado produtos. 

 
``` dart linenums="1" 
import 'package:custom_app/custom_app/web_app/web_app.imports.dart';
import 'package:flutter/material.dart';
import '../modulos.imports.dart';


class UsuariosView extends WebAppWidget {
  @override
  String displayName;

  @override
  WebAppModulo modulo;

  UsuariosController usuariosController = UsuariosController();


  UsuariosView({
    this.displayName,
    @required this.modulo,
  });

  @override
  Widget buildView(BuildContext context) {
    return Container(); 
  }
}

```




## 3. Publicar o modulo