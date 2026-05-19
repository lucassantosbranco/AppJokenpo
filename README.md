🚀 Como Começar
📋 Pré-requisitos

✅ Android Studio (versão 2021.1 ou superior)
✅ Android SDK 21+
✅ Java 8+
✅ Conexão com internet (para sincronizar dependências)

⚙️ Instalação
1️⃣ Clonar o Repositório
bashgit clone https://github.com/seu-usuario/AppJokenpo.git
cd AppJokenpo
2️⃣ Abrir no Android Studio

Abra o Android Studio
Clique em File → Open
Selecione a pasta do projeto
Aguarde a sincronização

3️⃣ Executar
bash# Via terminal
./gradlew assembleDebug

# Ou clique em Run (▶) no Android Studio
4️⃣ Instalar em Dispositivo/Emulador
bashadb install build/outputs/apk/debug/app-debug.apk

📖 Guia de Uso
🎮 Como Jogar

Escolha sua jogada - Clique em um dos 3 botões

🟡 Pedra
🔴 Papel
🔵 Tesoura


Veja o resultado - O app escolhe aleatoriamente
Acompanhe o placar - Vitórias aparecem em tempo real
Jogar novamente - Clique em qualquer botão ou use "Reiniciar Jogo"

📊 Regras do Jogo
Você EscolheApp EscolheResultado🪨 Pedra✂️ Tesoura✅ VOCÊ GANHA🪨 Pedra📄 Papel❌ VOCÊ PERDE🪨 Pedra🪨 Pedra🤝 EMPATE📄 Papel🪨 Pedra✅ VOCÊ GANHA📄 Papel✂️ Tesoura❌ VOCÊ PERDE📄 Papel📄 Papel🤝 EMPATE✂️ Tesoura📄 Papel✅ VOCÊ GANHA✂️ Tesoura🪨 Pedra❌ VOCÊ PERDE✂️ Tesoura✂️ Tesoura🤝 EMPATE

📁 Estrutura do Projeto
AppJokenpo/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/br/ulbra/appjokenpo/
│   │       │   └── MainActivity.java          # Lógica principal do jogo
│   │       ├── res/
│   │       │   ├── drawable/
│   │       │   │   ├── btn_round_yellow.xml   # Botão Pedra
│   │       │   │   ├── btn_round_red.xml      # Botão Papel
│   │       │   │   └── btn_round_blue.xml     # Botão Tesoura
│   │       │   ├── layout/
│   │       │   │   └── activity_main.xml      # Interface
│   │       │   └── values/
│   │       │       └── strings.xml
│   │       └── AndroidManifest.xml
│   ├── build.gradle
│   └── ...
├── build.gradle
├── settings.gradle
└── README.md

💻 Tecnologia Usada
Linguagens e Frameworks

Linguagem: Java 8+
Framework: Android Framework / AndroidX
API Mínima: Android 5.0 (API 21)
API Alvo: Android 13+ (API 33+)

Componentes Android Utilizados
ComponenteUsoActivityTela principal do aplicativoTextViewExibir textos (placar, resultado)ImageViewMostrar escolha do app (cores)ImageButtonBotões para selecionar opçõesLinearLayoutOrganizar elementos na tela
Bibliotecas
gradledependencies {
    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
    implementation 'com.google.android.material:material:1.9.0'
}

🔧 Configuração Detalhada
build.gradle (app)
gradleandroid {
    compileSdk 33

    defaultConfig {
        applicationId "br.ulbra.appjokenpo"
        minSdk 21
        targetSdk 33
        versionCode 1
        versionName "1.0.0"
    }
}
AndroidManifest.xml
xml<manifest package="br.ulbra.appjokenpo">
    <application
        android:label="@string/app_name"
        android:theme="@style/Theme.AppJokenpo">
        
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>

📚 Documentação do Código
MainActivity.java - Métodos Principais
onCreate(Bundle savedInstanceState)
java// Inicializa a activity e o placar
Chamado quando a aplicação é iniciada
selecionadoPedra/Papel/Tesoura(View view)
java// Chamados quando o usuário clica em um botão
Passam a opção para o método principal
opcaoSelecionado(String opcaoSelecionada)
java// Método principal - lida com toda a lógica do jogo
- Gera escolha aleatória para o app
- Compara com a escolha do jogador
- Atualiza placar
- Exibe resultado
atualizarPlacar()
java// Atualiza a exibição do placar na tela
Chamado após cada rodada
reiniciarJogo(View view)
java// Reset completo
- Placar volta a 0
- Cores/imagens são resetadas
- Resultado volta a "???"

🎨 Customização
Mudar Cores dos Botões
Edite os arquivos em res/drawable/:
btn_round_yellow.xml (Pedra)
xml<solid android:color="#FFD700" />  <!-- Altere este valor -->
btn_round_red.xml (Papel)
xml<solid android:color="#EE5A6F" />  <!-- Altere este valor -->
btn_round_blue.xml (Tesoura)
xml<solid android:color="#5DADE2" />  <!-- Altere este valor -->
Adicionar Imagens PNG

Renomeie suas imagens para:

pedra.png
papel.png
tesoura.png


Coloque em res/drawable/
No MainActivity.java, descomente:

javacase "pedra":
    imageResultado.setImageResource(R.drawable.pedra);
    break;

Comente as linhas de cor:

java// imageResultado.setBackgroundColor(0xFF808080);

🐛 Troubleshooting
Erro: "Cannot find symbol R.layout.activity_main"
Solução:

Verifique se o arquivo activity_main.xml existe em res/layout/
Faça um Build → Clean Project
Sincronize o Gradle

Erro: "' . ' is not a valid resource name"
Solução:

Nomes de drawable devem ter apenas: letras minúsculas, números e underscore
Corrija para: pedra.png (não pedra.png.png)

Botões não funcionam
Solução:

Verifique se o atributo android:onClick está definido no XML
Certifique-se que os métodos correspondentes existem na Activity

App não inicia
Solução:

Verifique o Logcat para mensagens de erro
Confirme que MainActivity está declarada no AndroidManifest.xml
Aumente a RAM do emulador se necessário


📱 Compatibilidade
RecursoSuporteAndroid 5.0 (API 21)✅Android 6.0 (API 23)✅Android 10 (API 29)✅Android 12 (API 31)✅Android 13 (API 33)✅Modo Noturno✅Rotação de Tela✅

🎯 Possíveis Melhorias

 Adicionar animações ao clicar
 Som de vitória/derrota
 Histórico de partidas
 Estatísticas detalhadas
 Diferentes temas (claro/escuro)
 Multiplayer (local)
 Ranking online
 Modos de dificuldade

