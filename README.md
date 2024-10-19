VIDEO 1: Introdução ao Flutter
O que é Flutter?
Flutter é um framework opensource que permite o desenvolvimento rápido de interfaces de usuário belas e nativas para dispositivos móveis, web e desktop, utilizando uma linguagem de programação única, o Dart. Sua arquitetura centrada em widgets facilita a construção de interfaces consistentes e altamente customizáveis, enquanto a eficiência do código permite que os desenvolvedores alcancem uma variedade de plataformas com facilidade.

INSTALAÇÃO DO FLUTTER
Baixe o Flutter SDK

Acesse o site oficial do Flutter: Flutter SDK
Selecione a versão para Windows e faça o download.
Configuração do Flutter SDK

Extraia o arquivo baixado para um local apropriado no seu sistema (por exemplo, C:\src\flutter).
Adicione o caminho do Flutter ao PATH do sistema:
Vá em Variáveis de Ambiente e adicione C:\src\flutter\bin ao Path.
Teste a instalação no Prompt de Comando com:
css
Copiar código
flutter version
dart version
INSTALAÇÃO DO SDK DO ANDROID (SEM ANDROID STUDIO)
Download e Configuração do SDK

Acesse o link para o SDK do Android: Android SDK Commandline Tools
Na seção Command line tools only, baixe a versão apropriada para Windows.
Extraia o arquivo e mova para uma pasta, por exemplo, C:\Android\cmdlinetools.
Adicionar o Android SDK ao PATH

Crie uma nova variável de ambiente chamada ANDROID_HOME e defina como o caminho para a pasta onde você extraiu o SDK (C:\Android\cmdlinetools).
Adicione também C:\Android\cmdlinetools\bin e C:\Android\platformtools ao Path.
Instale Componentes Necessários do SDK

No terminal, use o comando:
arduino
Copiar código
sdkmanager "platformtools" "platforms;android33" "buildtools;33.0.0"
CONFIGURAÇÃO DO EMULADOR ANDROID COM BLUESTACKS
Instalação do BlueStacks

Acesse o site do BlueStacks: BlueStacks
Baixe e instale o BlueStacks no seu computador.
Durante a instalação, siga as instruções na tela e clique em "Próximo" até concluir a instalação.
Configuração do BlueStacks para Flutter

Ativar Depuração no BlueStacks:
Abra o BlueStacks e vá para Configurações (ícone de engrenagem no canto superior direito) → Preferências → Avançado.
Ative a Depuração Android.
Salve as mudanças.
Ajustar Desempenho do Emulador:
Nas configurações, ajuste a performance para melhorar a execução dos seus aplicativos:
CPU: Selecione o máximo de núcleos disponíveis.
RAM: Aumente a memória RAM, se possível, para pelo menos 4 GB.
Reinicie o BlueStacks para aplicar as configurações.
Conectar o BlueStacks com Flutter usando ADB

Certifiquese de que o ADB (Android Debug Bridge) esteja instalado. Se não estiver, instale usando o comando:
arduino
Copiar código
sdkmanager "platformtools"
No terminal, adicione o BlueStacks como um dispositivo detectável:
arduino
Copiar código
adb connect 127.0.0.1:5555
Verifique se o dispositivo foi conectado com sucesso usando:
Copiar código
adb devices
Agora, o BlueStacks deve aparecer na lista de dispositivos, permitindo que você o utilize como um emulador para testar seus aplicativos Flutter.
INSTALAÇÃO DO VISUAL STUDIO CODE (VS Code)
Extensões do Flutter e Dart
Certifiquese de que o VS Code está instalado.
Instale as extensões: Flutter e Dart para facilitar o desenvolvimento.
TUTORIAL: Desenvolvimento do Primeiro Aplicativo Flutter  Aplicação Padrão
Criar um Novo Projeto Flutter

No terminal, execute:
bash
Copiar código
flutter create my_first_flutter_app
cd my_first_flutter_app
Executar a Aplicação Padrão

Certifique-se de que o BlueStacks esteja aberto e funcionando.
No terminal, inicie o projeto:
arduino
Copiar código
flutter run
Se tudo estiver configurado corretamente, o aplicativo Flutter será executado no BlueStacks.
Com essas etapas, você pode configurar e testar seu ambiente Flutter sem a necessidade de instalar o Android Studio completo, utilizando o BlueStacks como emulador Android e o SDK necessário para compilar e executar seus projetos.



 VIDEO 2   Fundamentos do Dart

 Variáveis e Tipos de Dados
 Declaração de Variáveis: em Dart, você pode declarar variáveis usando var, final ou const.

 var: para variáveis que podem mudar.
 final: para variáveis que podem ser definidas uma vez e não podem ser alteradas.
 const: para constantes em tempo de compilação.

 Tipos de Dados
 Dart possui tipos de dados básicos como int, double, String, bool, entre outros.

 Controle de Fluxo
 Estruturas Condicionais
 Utilizamos if, else if e else para controle de fluxo.

 Loops
 Dart possui várias estruturas de loop, como for, while, e dowhile.

 Funções e Métodos
 Definição de Funções: As funções em Dart são definidas com a palavrachave void (ou o tipo de retorno). Elas podem ter parâmetros e retornar valores.

 Classes e Objetos
 Definição de Classes: Dart é uma linguagem orientada a objetos. Você pode criar classes e instanciar objetos.


 CODIGO

// Classe Aluno
class Aluno {

//usando os tipos de dados
  String nome;           // Nome do aluno
  List<double> notas;    // Lista de notas do aluno

  // Construtor da classe Aluno
  Aluno(this.nome) : notas = []; // Inicializa a lista de notas

  // Método para adicionar uma nota
  void adicionarNota(double nota) {
    notas.add(nota); // Adiciona a nota à lista
  }

  // Método para calcular a média das notas
  double calcularMedia() {
    double soma = 0;
    for (var nota in notas) {
      soma += nota; // Soma todas as notas
    }
    return soma / notas.length; // Retorna a média
  }

  // Método para verificar se o aluno foi aprovado
  bool foiAprovado() {
    return calcularMedia() >= 7; // Aprovação com média >= 7
  }
}

void main() {
  // Criando um objeto Aluno
  var aluno = Aluno('João');

  // Adicionando notas
  aluno.adicionarNota(6.5);
  aluno.adicionarNota(8.0);
  aluno.adicionarNota(7.5);

  // Calculando a média
  double media = aluno.calcularMedia();
  print('Média de ${aluno.nome}: $media');

  // Verificando se o aluno foi aprovado
  if (aluno.foiAprovado()) {
    print('${aluno.nome} foi aprovado.');
  } else {
    print('${aluno.nome} foi reprovado.');
  }
}


Passo a Passo do Código

1. Definição da Classe Aluno

class Aluno {
  String nome;           // Nome do aluno
  List<double> notas;    // Lista de notas do aluno
Classe Aluno: Estamos criando uma classe chamada Aluno que representa um estudante.
Propriedades:
nome: Armazena o nome do aluno como uma string.
notas: Uma lista que armazenará as notas do aluno como números de ponto flutuante (double).
2. Construtor da Classe

  // Construtor da classe Aluno
  Aluno(this.nome) : notas = []; // Inicializa a lista de notas
Construtor: É uma função especial chamada quando criamos uma nova instância da classe. Aqui, estamos passando o nome do aluno como parâmetro e inicializando notas como uma lista vazia.
3. Método para Adicionar uma Nota

  // Método para adicionar uma nota
  void adicionarNota(double nota) {
    notas.add(nota); // Adiciona a nota à lista
  }
Método adicionarNota: Este método permite adicionar uma nova nota à lista notas. Ele recebe um parâmetro nota e a adiciona à lista usando notas.add(nota).
4. Método para Calcular a Média

  // Método para calcular a média das notas
  double calcularMedia() {
    double soma = 0;
    for (var nota in notas) {
      soma += nota; // Soma todas as notas
    }
    return soma / notas.length; // Retorna a média
  }
Método calcularMedia: Este método calcula a média das notas.
Inicializa uma variável soma com 0.
Usa um loop for para iterar sobre cada nota na lista notas, somandoas.
Retorna a média dividindo a soma pelo número total de notas (notas.length).
5. Método para Verificar Aprovação

  // Método para verificar se o aluno foi aprovado
  bool foiAprovado() {
    return calcularMedia() >= 7; // Aprovação com média >= 7
  }
}
Método foiAprovado: Este método verifica se o aluno foi aprovado.
Chama o método calcularMedia() e verifica se a média é maior ou igual a 7.
Retorna true se aprovado e false caso contrário.
6. Função Principal main

void main() {
  // Criando um objeto Aluno
  var aluno = Aluno('João');
Função main: É o ponto de entrada do programa. Aqui, criamos uma instância da classe Aluno, passando o nome "João".
7. Adicionando Notas

  // Adicionando notas
  aluno.adicionarNota(6.5);
  aluno.adicionarNota(8.0);
  aluno.adicionarNota(7.5);
Chamamos o método adicionarNota três vezes para adicionar as notas 6.5, 8.0 e 7.5 à lista de notas do aluno.
8. Calculando a Média

  // Calculando a média
  double media = aluno.calcularMedia();
  print('Média de ${aluno.nome}: $media');
Calculamos a média chamando calcularMedia() e armazenamos o resultado na variável media.
Em seguida, imprimimos a média do aluno.
9. Verificando a Aprovação

  // Verificando se o aluno foi aprovado
  if (aluno.foiAprovado()) {
    print('${aluno.nome} foi aprovado.');
  } else {
    print('${aluno.nome} foi reprovado.');
  }
}
Usamos uma estrutura condicional if para verificar se o aluno foi aprovado chamando o método foiAprovado().
Imprimimos uma mensagem indicando se o aluno foi aprovado ou reprovado.




 VIDEO 3  Widgets no Flutter

 StatefulWidget e StatelessWidget

Explicação Teórica:

StatelessWidget: Um widget que não mantém estado. Sua interface é imutável e é construído apenas uma vez.
StatefulWidget: Um widget que mantém estado e pode ser alterado ao longo do tempo. Ele se reconstruirá quando o estado mudar. 

Código Exemplo:
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

// Modelo de estado que gerencia o contador
class Contador with ChangeNotifier {
  int _valor = 0;

  int get valor => _valor;

  void incrementar() {
    _valor++;
    notifyListeners(); // Notifica os ouvintes sobre a mudança
  }
}

// Ponto de entrada da aplicação
void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => Contador(),
      child: MeuApp(),
    ),
  );
}

// Classe principal do aplicativo
class MeuApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Gerenciamento de Estado',
      home: TelaContador(),
    );
  }
}

// Classe que representa a tela do contador
class TelaContador extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final contador = Provider.of<Contador>(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('Contador'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'Valor do contador:',
              style: TextStyle(fontSize: 20),
            ),
            Text(
              '${contador.valor}',
              style: TextStyle(fontSize: 40),
            ),
            ElevatedButton(
              onPressed: contador.incrementar,
              child: Text('Incrementar'),
            ),
          ],
        ),
      ),
    );
  }
}



Demonstração Visual:

Execute o código acima em um emulador como o BlueStacks ou em um dispositivo real.
O primeiro texto mostrará a mensagem de um StatelessWidget e abaixo você verá o contador do StatefulWidget com um botão para incrementálo.

 Layouts: Row, Column, Stack

Explicação Teórica:

Row: Organiza seus filhos em uma linha horizontal.
Column: Organiza seus filhos em uma coluna vertical.
Stack: Permite empilhar widgets uns sobre os outros.

Código Exemplo:
 // Ponto de entrada da aplicação
void main() {
  runApp(
    // Inicia o aplicativo Flutter
    MaterialApp(
      home: Scaffold(
        // Cria uma estrutura básica de tela com AppBar e corpo
        appBar: AppBar(
          title: Text('Layouts Exemplo'), // Título da AppBar
        ),
        body: Stack(
          // Utiliza um Stack para empilhar widgets
          children: [
            Container(
              // Primeiro widget na pilha (fundo)
              color: Colors.blue, // Define a cor de fundo como azul
              width: 200, // Largura do container
              height: 200, // Altura do container
            ),
            Positioned(
              // Widget posicionado em relação ao Stack
              top: 50, // Posição a partir do topo
              left: 50, // Posição a partir da esquerda
              child: Container(
                // Segundo widget na pilha (sobreposição)
                color: Colors.red, // Define a cor do container como vermelho
                width: 100, // Largura do container
                height: 100, // Altura do container
              ),
            ),
          ],
        ),
      ),
    ),
  );
}


Demonstração Visual: 

Ao executar, você verá um quadrado azul com um quadrado vermelho sobreposto.
Experimente mudar a posição do quadrado vermelho alterando os valores de top e left em Positioned.

 Navegação entre Páginas (Navigator):

Explicação Teórica:

O Navigator é usado para gerenciar a pilha de páginas na aplicação. Permite navegar entre diferentes telas.

Código Exemplo: 
// Ponto de entrada da aplicação
void main() {
  runApp(
    // Inicia o aplicativo Flutter
    MaterialApp(
      home: TelaInicial(), // Define a tela inicial como TelaInicial
    ),
  );
}

// Classe que representa a tela inicial
class TelaInicial extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // Cria uma estrutura básica de tela com AppBar e corpo
      appBar: AppBar(
        title: Text('Tela Inicial'), // Título da AppBar
      ),
      body: Center(
        child: ElevatedButton(
          // Botão que leva à segunda tela
          onPressed: () {
            // Ação quando o botão é pressionado
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SegundaTela()), // Navega para a SegundaTela
            );
          },
          child: Text('Ir para Segunda Tela'), // Texto do botão
        ),
      ),
    );
  }
}

// Classe que representa a segunda tela
class SegundaTela extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // Cria uma estrutura básica de tela para a segunda tela
      appBar: AppBar(
        title: Text('Segunda Tela'), // Título da AppBar
      ),
      body: Center(
        child: ElevatedButton(
          // Botão que volta para a tela anterior
          onPressed: () {
            Navigator.pop(context); // Volta para a tela anterior
          },
          child: Text('Voltar'), // Texto do botão
        ),
      ),
    );
  }
}

Demonstração Visual: 

Ao executar, você verá a Tela Inicial com um botão. Ao clicar, você irá para a Segunda Tela e poderá voltar.

 Formulários e Validação

Explicação Teórica: 

Widgets de formulário permitem coletar entradas do usuário. A validação garante que os dados estejam corretos antes de serem processados.

Código Exemplo: 
// Classe que representa o formulário
class MeuFormulario extends StatefulWidget {
  @override
  _MeuFormularioState createState() => _MeuFormularioState(); // Cria o estado associado ao formulário
}

// Classe que contém o estado do MeuFormulario
class _MeuFormularioState extends State<MeuFormulario> {
  final _formKey = GlobalKey<FormState>(); // Chave global para o formulário
  String? nome; // Variável para armazenar o nome

  @override
  Widget build(BuildContext context) {
    return Form(
      key: _formKey, // Associa a chave ao formulário
      child: Column(
        // Organiza os filhos verticalmente
        children: [
          TextFormField(
            decoration: InputDecoration(labelText: 'Nome'), // Texto de rótulo do campo
            validator: (value) {
              // Valida o valor inserido no campo
              if (value == null || value.isEmpty) {
                return 'Por favor, insira seu nome'; // Mensagem de erro se o campo estiver vazio
              }
              return null; // Retorna null se a validação passar
            },
            onSaved: (value) {
              nome = value; // Salva o valor do campo na variável nome
            },
          ),
          ElevatedButton(
            onPressed: () {
              // Ação quando o botão é pressionado
              if (_formKey.currentState!.validate()) {
                // Valida o formulário
                _formKey.currentState!.save(); // Salva os dados do formulário
                // Aqui você pode processar o nome
                print('Nome: $nome'); // Imprime o nome no console
              }
            },
            child: Text('Enviar'), // Texto do botão
          ),
        ],
      ),
    );
  }
}

// Ponto de entrada da aplicação
void main() {
  runApp(MaterialApp(
    home: Scaffold(
      appBar: AppBar(title: Text('Formulário Exemplo')), // Título da AppBar
      body: MeuFormulario(), // Adiciona o MeuFormulario ao corpo da Scaffold
    ),
  ));
}

Demonstração Visual: 

Ao executar, você verá um campo de texto para inserir o nome. Ao clicar em "Enviar", ele validará se o campo está preenchido e, se sim, imprimirá o nome.



 VIDEO 4  Gerenciamento de Estado

Método de Gerenciamento de Estado: Utilizaremos o Provider

 Criando o Projeto: 

flutter create gerenciador_estado
cd gerenciador_estado

 Configurando o Provider (Adicione a dependência do Provider no pubspec.yaml):

dependencies:
  flutter:
    sdk: flutter
  provider: ^6.0.0


Execute flutter pub get para instalar as dependências.


Criando o Modelo de Estado

Crie um arquivo contador.dart:
// Importa a biblioteca necessária para usar ChangeNotifier
import 'package:flutter/foundation.dart';

// Classe Contador que estende ChangeNotifier para notificar ouvintes sobre mudanças
class Contador with ChangeNotifier {
  // Variável privada para armazenar o valor do contador
  int _valor = 0;

  // Getter para acessar o valor do contador
  int get valor => _valor;

  // Método para incrementar o valor do contador
  void incrementar() {
    _valor++; // Incrementa o valor do contador
    notifyListeners(); // Notifica todos os ouvintes que o valor foi alterado
  }
}


Criando a Interface do Usuário

No main.dart, configure o Provider e crie a interface:// Importa os pacotes necessários
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import 'contador.dart'; // Importa o modelo de estado Contador

// Ponto de entrada da aplicação
void main() {
  runApp(
    // Cria um ChangeNotifierProvider para gerenciar o estado
    ChangeNotifierProvider(
      create: (context) => Contador(), // Cria uma instância de Contador
      child: MeuApp(), // Inicia o aplicativo com MeuApp
    ),
  );
}

// Classe principal do aplicativo
class MeuApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Gerenciamento de Estado', // Título da aplicação
      home: TelaContador(), // Define a tela inicial como TelaContador
    );
  }
}

// Classe que representa a tela do contador
class TelaContador extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Acessa o modelo de estado Contador usando o Provider
    final contador = Provider.of<Contador>(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('Contador'), // Título da AppBar
      ),
      body: Center(
        // Centraliza o conteúdo no corpo da tela
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center, // Centraliza verticalmente
          children: [
            Text(
              'Valor do contador: ${contador.valor}', // Exibe o valor atual do contador
              style: TextStyle(fontSize: 30), // Estilo do texto
            ),
            ElevatedButton(
              onPressed: contador.incrementar, // Chama o método incrementar ao pressionar
              child: Text('Incrementar'), // Texto do botão
            ),
          ],
        ),
      ),
    );
  }
}


Executando a Aplicação

Execute a aplicação em um emulador ou dispositivo físico: 



Tutorial Completo: Criando uma API REST para Livros em Node.js e Integrando com um Aplicativo Flutter
Parte 1: Criando a API REST com Node.js
Passo 1.1: Instalar o Node.js
Verifique se você tem o Node.js instalado na sua máquina. Você pode baixálo em nodejs.org.
Para confirmar a instalação, execute:
bash
Copiar código
node v
Passo 1.2: Criar um Novo Projeto Node.js
Crie um diretório para o projeto:

bash
Copiar código
mkdir biblioteca_api
cd biblioteca_api
Inicialize um novo projeto Node.js:

bash
Copiar código
npm init y
Passo 1.3: Instalar as Dependências Necessárias
Instale os pacotes que utilizaremos:
bash
Copiar código
npm install express bodyparser cors fs
express: Framework para facilitar a criação de APIs.
bodyparser: Middleware para processar dados JSON.
cors: Permite requisições de diferentes origens (útil para integração com Flutter).
fs: Para manipulação de arquivos.
Passo 1.4: Criar o Arquivo db.json
Na raiz do projeto, crie um arquivo chamado db.json com o seguinte conteúdo:
json
Copiar código
{
  "livros": []
}
Este arquivo servirá como um banco de dados simples para armazenar informações sobre os livros.
Passo 1.5: Configurar o Servidor Node.js
Crie o arquivo server.js:

Adicione o seguinte código ao server.js:
javascript
Copiar código
const express = require('express');
const bodyParser = require('bodyparser');
const cors = require('cors');
const fs = require('fs');
const app = express();
const PORT = 3000;

app.use(cors());
app.use(bodyParser.json());

const readData = () => {
  const data = fs.readFileSync('db.json');
  return JSON.parse(data);
};

const writeData = (data) => {
  fs.writeFileSync('db.json', JSON.stringify(data, null, 2));
};

// Obter todos os livros
app.get('/livros', (req, res) => {
  const data = readData();
  res.json(data.livros);
});

// Adicionar um novo livro
app.post('/livros', (req, res) => {
  const data = readData();
  const novoLivro = { id: Date.now().toString(), titulo: req.body.titulo, autor: req.body.autor };
  data.livros.push(novoLivro);
  writeData(data);
  res.status(201).json(novoLivro);
});

// Remover um livro
app.delete('/livros/:id', (req, res) => {
  const data = readData();
  const livrosFiltrados = data.livros.filter(livro => livro.id !== req.params.id);
  writeData({ livros: livrosFiltrados });
  res.status(204).send();
});

// Iniciar o servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
Inicie o servidor:

Execute o comando:
bash
Copiar código
node server.js
O servidor estará disponível em http://localhost:3000.
Parte 2: Integrar o Código com um Aplicativo Flutter
Passo 2.1: Preparar o Projeto Flutter
Crie um novo projeto Flutter:

bash
Copiar código
flutter create meu_app_livros
Navegue até o diretório do projeto:
bash
Copiar código
cd meu_app_livros
Adicionar dependências no pubspec.yaml:

Abra o arquivo pubspec.yaml e adicione:
yaml
Copiar código
dependencies:
  flutter:
    sdk: flutter
  http: ^0.13.3
Execute flutter pub get para instalar as dependências.
Passo 2.2: Criar um Modelo de Livro
Crie o arquivo livro.dart:
No diretório lib, crie um arquivo livro.dart:
dart
Copiar código
class Livro {
  String id;
  String titulo;
  String autor;

  Livro({required this.id, required this.titulo, required this.autor});

  factory Livro.fromJson(Map<String, dynamic> json) {
    return Livro(
      id: json['id'],
      titulo: json['titulo'],
      autor: json['autor'],
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'titulo': titulo,
      'autor': autor,
    };
  }
}
Passo 2.3: Criar o Serviço para Comunicação com a API
Crie o arquivo servico_biblioteca.dart:
Crie servico_biblioteca.dart no diretório lib e adicione:
dart
Copiar código
import 'dart:convert';
import 'package:http/http.dart' as http;
import 'livro.dart';

class ServicoBiblioteca {
  final String baseUrl = 'http://localhost:3000/livros';

  Future<List<Livro>> lerLivros() async {
    final response = await http.get(Uri.parse(baseUrl));
    if (response.statusCode == 200) {
      final List<dynamic> jsonList = json.decode(response.body);
      return jsonList.map((livro) => Livro.fromJson(livro)).toList();
    } else {
      throw Exception('Erro ao carregar livros');
    }
  }

  Future<void> criarLivro(Livro livro) async {
    final response = await http.post(
      Uri.parse(baseUrl),
      headers: {'ContentType': 'application/json'},
      body: json.encode(livro.toJson()),
    );
    if (response.statusCode != 201) {
      throw Exception('Erro ao criar livro');
    }
  }

  Future<void> deletarLivro(String id) async {
    final response = await http.delete(Uri.parse('$baseUrl/$id'));
    if (response.statusCode != 204) {
      throw Exception('Erro ao deletar livro');
    }
  }
}
Passo 2.4: Integrar o Serviço com a Interface Flutter
Criar Interface para Listar e Adicionar Livros:
Modifique o main.dart para exibir uma lista de livros e um formulário para adicionar novos livros:
dart
Copiar código
import 'package:flutter/material.dart';
import 'servico_biblioteca.dart';
import 'livro.dart';

void main() {
  runApp(MeuAppLivros());
}

class MeuAppLivros extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: TelaInicial(),
    );
  }
}

class TelaInicial extends StatefulWidget {
  @override
  _TelaInicialState createState() => _TelaInicialState();
}

class _TelaInicialState extends State<TelaInicial> {
  final ServicoBiblioteca _servicoBiblioteca = ServicoBiblioteca();
  final TextEditingController _controllerTitulo = TextEditingController();
  final TextEditingController _controllerAutor = TextEditingController();
  List<Livro> _livros = [];

  @override
  void initState() {
    super.initState();
    _carregarLivros();
  }

  void _carregarLivros() async {
    final livros = await _servicoBiblioteca.lerLivros();
    setState(() {
      _livros = livros;
    });
  }

  void _adicionarLivro() async {
    final novoLivro = Livro(id: '', titulo: _controllerTitulo.text, autor: _controllerAutor.text);
    await _servicoBiblioteca.criarLivro(novoLivro);
    _carregarLivros();
    _controllerTitulo.clear();
    _controllerAutor.clear();
  }

  void _deletarLivro(String id) async {
    await _servicoBiblioteca.deletarLivro(id);
    _carregarLivros();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Biblioteca')),
      body: Column(
        children: [
          TextField(
            controller: _controllerTitulo,
            decoration: InputDecoration(labelText: 'Título do Livro'),
          ),
          TextField(
            controller: _controllerAutor,
            decoration: InputDecoration(labelText: 'Autor do Livro'),
          ),
          ElevatedButton(
            onPressed: _adicionarLivro,
            child: Text('Adicionar Livro'),
          ),
          Expanded(
            child: ListView.builder(
              itemCount: _livros.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(_livros[index].titulo),
                  subtitle: Text(_livros[index].autor),
                  trailing: IconButton(
                    icon: Icon(Icons.delete),
                    onPressed: () => _deletarLivro(_livros[index].id),
                  ),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
Passo 2.5: Executar o Aplicativo Flutter
Execute o aplicativo Flutter:
bash
Copiar código
flutter run
O aplicativo deve estar rodando e você deve conseguir adicionar e listar livros através da interface.
Considerações Finais
Testes: Para garantir que tudo está funcionando, você pode usar ferramentas como Postman ou Insomnia para testar a API REST antes de integrála ao Flutter.
Melhorias: Considere adicionar mais funcionalidades, como edição de livros, paginar a lista de livros ou implementar autenticação.
Com este guia, você deve ser capaz de criar uma API REST simples em Node.js para gerenciar livros e integrar essa API em um aplicativo Flutter. Se você tiver dúvidas ou precisar de mais ajuda, fique à vontade para perguntar!