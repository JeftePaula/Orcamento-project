# Orcamento-project

## [link do projeto em execução](https://jeftepaula.github.io/Orcamento-project)

![imagem home page](https://github.com/JeftePaula/Orcamento-project/blob/main/Captura%20de%20tela%202023-02-13%20154436.png)

### Sobre o projeto:
  
  Projeto feito por mim utilizando Javascript, html e bootstrap. O foco do projeto nao era o css, entao optei por um design mais simples e o bootstrap no lugar da codificação css.
  Como um projeto para praticar a *__Orientação a objetos em Js__*, o foco do projeto é a *__POO__*, além disso, devido ao fato de ainda não ter conhecimentos sólidos com banco de dados, simulei um usando uma classe e armazenamento local com Jason.

<hr/>

### Classe em destaque
  ```
    class Bd
    {
    
    //construtor
    constructor(){
        let id =  localStorage.getItem('id');
        if(id === null){
            localStorage.setItem('id', 0);
        }
    }
    
    //organiza os id's para salvar em local Storage sem sobrescrição
    getProximoId(){
        let ProximoId = localStorage.getItem('id');
        return parseInt(ProximoId) + 1;
    }
    
    //recebe uma despesa e armazena em id
    gravar(d){
        let id = this.getProximoId();
        
        localStorage.setItem(id, JSON.stringify(d));
        localStorage.setItem('id', id);
    }
    //codigo para a exibição na pagina de consultas
    recuperarTodosRegistros(){
        let despesas = Array();
        
        let id = localStorage.getItem('id');
        
        for(let i = 1; i <= id; i++){
            let despesa = JSON.parse(localStorage.getItem(i));
            if(despesa === null) continue;
            despesa.id = i;
            despesas.push(despesa);
        }
        return despesas;
    }
    
    //metodo para pesquisar depesa especifica
    pesquisar(despesa){
        let despesasFiltradas = Array();
        despesasFiltradas = this.recuperarTodosRegistros();
        
        if(despesa.ano != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.ano == despesa.ano);
        }

        if(despesa.mes != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.mes == despesa.mes);
        }

        if(despesa.dia != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.dia == despesa.dia);
        }

        if(despesa.tipo != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.tipo == despesa.tipo);
        }

        if(despesa.descricao != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.descricao == despesa.descricao);
        }

        if(despesa.valor != ''){
            despesasFiltradas = despesasFiltradas.filter(d => d.valor == despesa.valor);
        }
        return despesasFiltradas;
    }
    
    //remocao de despesas
    remover(id){
        localStorage.removeItem(id);
    }
}
    
  ```
<hr/>

  ### Desafios enfrentados
  * Gravar dados localmente
  * Manipulação do DOM
  * Exclusão de despesas

<hr/>

  ### Como usar o site?
  * Preencha os campos de acordo com as respectivas informações
  * clique no '+' em azul para cadastrar a despesa
  * se a despesa for cadastrada corretamente, voce receberá uma mensagem informando
  * Para consultar as despesas clique em 'consulta' no canto superior esquerdo
  * caso queira recuperar alguma consulta em especifico, basta descreve-la nos respectivos campos e apertar na 🔎

<hr/>

  ### Proximas atualizações
  - [ ] Adicionar um banco de dados
  - [ ] Adicionar anos dinamicos
  - [ ] Adicionar validação de dados para dia
