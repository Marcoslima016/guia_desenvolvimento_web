#PageAreas

## Introdução
Como o proprio nome ja diz, PageAreas são regiões que ocuparão uma parcela da página. Essas regiões podem ser simples delimitações de espaço sem funcionalidade, ou podem até mesmo ser algum elemento funcional da tela como por exemplo relatórios.  

Utilização: PageAreas são instanciadas dentro do metodo BuildView(Context) presente na view do modulo. 

---

## Principais PageAreas disponiveis: 

### 1. Blank 

### 2. BasicReport (Relatório básico)

Relatório simples onde apenas são disponibilizadas as informações, sem haver uma interação avançada do usuário com o relatório.  

##### Exemplo de utilização: 

``` dart  linenums="1"
  @override
  Widget buildView(BuildContext context) {
    return BasicReport(
      colunas: [
        ReportColumn(displayName: "Email", id: "email"),
        ReportColumn(displayName: "Nome", id: "nome"),
        ReportColumn(displayName: "idade", id: "idade"),
      ],
      source: ReportDatasource.tableName(table: "usuarios"),
    );
  }

```

No exemplo acima, foi definido um BasicReport dentro do metodo buildView() que esta presente na camada View do modulo. Foi simulado um relatório que exibe dados de uma tabela que armazena dados dos usuarios (tabela "usuarios"), e foram definidas as colunas email, nome e idade. 
### 3. AdvancedReport 