# 🎮 App Jokenpo Mobile

Um aplicativo Android interativo do clássico jogo Pedra, Papel e Tesoura (Jokenpo), permitindo ao usuário jogar contra o aplicativo com geração aleatória de escolhas, placar dinâmico e feedback visual imediato.

---

## 🎯 Objetivo do Aplicativo

Desenvolver um aplicativo Android divertido e interativo que implementa o jogo de Jokenpo (Pedra, Papel, Tesoura), com lógica de decisão, geração aleatória de respostas do aplicativo e sistema de pontuação em tempo real.

---

## ✨ Funcionalidades Principais

- ✅ **Três Opções de Jogo** - Pedra, Papel e Tesoura disponíveis
- ✅ **Escolha Aleatória** - Aplicativo escolhe aleatoriamente sua jogada
- ✅ **Comparação de Resultado** - Determina vencedor, perdedor ou empate
- ✅ **Placar Dinâmico** - Mantém pontuação do jogador e do aplicativo
- ✅ **Feedback Visual** - ImageView exibe a escolha do app
- ✅ **Mensagens de Resultado** - TextView mostra o resultado da rodada
- ✅ **Reiniciar Jogo** - Botão para resetar placar e começar novo
- ✅ **Interface Intuitiva** - Design simples e responsivo

---

## 🎮 Regras do Jogo

### Como Funciona

O clássico Jokenpo segue estas regras simples:

| Situação | Resultado | Descrição |
|----------|-----------|-----------|
| **Pedra vs Tesoura** | Pedra Vence | Pedra quebra Tesoura |
| **Pedra vs Papel** | Papel Vence | Papel cobre Pedra |
| **Papel vs Tesoura** | Tesoura Vence | Tesoura corta Papel |
| **Pedra vs Pedra** | Empate | Mesma escolha |
| **Papel vs Papel** | Empate | Mesma escolha |
| **Tesoura vs Tesoura** | Empate | Mesma escolha |

### Matriz de Vitória

```
         JOGADOR
           P  Pa  T
      P   ✓  ✗  ✓
APP  Pa   ✓  ✓  ✗
      T   ✗  ✓  ✓

Legend: P=Pedra, Pa=Papel, T=Tesoura
✓ = Vence / ✗ = Perde
```

---

## 🏗️ Estrutura da Interface

### Layout Visual

```
┌────────────────────────────────────┐
│      JOKENPO - PEDRA, PAPEL E      │
│           TESOURA                  │
├────────────────────────────────────┤
│                                    │
│      Escolha do App:               │
│          [IMAGEM]                  │
│        (pedra/papel/tesoura)       │
│                                    │
│      Resultado: Você GANHOU! ;D    │
│                                    │
│      Placar:                       │
│      Você: 3    -    App: 2        │
│                                    │
│  [PEDRA]  [PAPEL]  [TESOURA]      │
│                                    │
│           │
└────────────────────────────────────┘
```

### Componentes da Interface

| Componente | Tipo | Descrição | ID |
|-----------|------|-----------|-----|
| Título | TextView | "Jokenpo - Pedra, Papel e Tesoura" | `tvTitulo` |
| Imagem App | ImageView | Exibe escolha do app | `imgApp` |
| Resultado | TextView | Mostra resultado da rodada | `txtResultado` |
| Placar | TextView | Exibe pontuação | `txtPlacar` |
| Botão Pedra | ImageButton/Button | Seleciona Pedra | `btnPedra` |
| Botão Papel | ImageButton/Button | Seleciona Papel | `btnPapel` |
| Botão Tesoura | ImageButton/Button | Seleciona Tesoura | `btnTesoura` |
| Botão Reiniciar | Button | Reinicia o jogo | `btnReiniciar` |

---

## 💡 Como Funciona

### 1. Seleção do Jogador

O jogador clica em um dos três botões (Pedra, Papel ou Tesoura):

```java
public void selecionadoPedra(View view) {
    this.opcaoSelecionado("pedra");
}

public void selecionadoPapel(View view) {
    this.opcaoSelecionado("papel");
}

public void selecionadoTesoura(View view) {
    this.opcaoSelecionado("tesoura");
}
```

**O que acontece:**
- Cada método é chamado via `android:onClick` no XML
- Passa a opção selecionada para o método principal

### 2. Escolha Aleatória do App

O aplicativo gera uma escolha aleatória:

```java
String opcoes[] = {"pedra", "papel", "tesoura"};
String opcaoApp = opcoes[new Random().nextInt(3)];
```

**O que acontece:**
- Um número aleatório entre 0 e 2 é gerado
- A opção correspondente é selecionada no array

### 3. Exibição da Escolha

A imagem da escolha do app é exibida:

```java
switch (opcaoApp) {
    case "pedra":
        imageResultado.setImageResource(R.drawable.pedra);
        break;
    case "papel":
        imageResultado.setImageResource(R.drawable.papel);
        break;
    case "tesoura":
        imageResultado.setImageResource(R.drawable.tesoura);
        break;
}
```

**O que aparece:**
- A imagem correspondente é carregada e exibida

### 4. Comparação e Resultado

O sistema verifica quem ganhou:

```java
// Aplicativo vence
if ((opcaoApp.equals("tesoura") && opcaoSelecionada.equals("papel")) ||
    (opcaoApp.equals("papel") && opcaoSelecionada.equals("pedra")) ||
    (opcaoApp.equals("pedra") && opcaoSelecionada.equals("tesoura"))) {
    txtResult.setText("Resultado: Você PERDEU... :(");
    pontuacaoApp++;
}
// Jogador vence
else if ((opcaoSelecionada.equals("tesoura") && opcaoApp.equals("papel")) ||
         (opcaoSelecionada.equals("papel") && opcaoApp.equals("pedra")) ||
         (opcaoSelecionada.equals("pedra") && opcaoApp.equals("tesoura"))) {
    txtResult.setText("Resultado: Você GANHOU... ;D");
    pontuacaoJogador++;
}
// Empate
else {
    txtResult.setText("Resultado: Vocês EMPATARAM... :|");
}
```

### 5. Atualização do Placar

O placar é atualizado após cada rodada:

```java
public void atualizarPlacar() {
    TextView txtPlacar = findViewById(R.id.txtPlacar);
    txtPlacar.setText("Você: " + pontuacaoJogador + " - App: " + pontuacaoApp);
}
```

---

## 🛠️ Tecnologias e Ferramentas

Para o desenvolvimento deste projeto, foram utilizadas:

- **Linguagem:** [Java](https://www.java.com/pt-BR/)
- **Layout:** XML (ConstraintLayout ou LinearLayout)
- **IDE:** [Android Studio](https://developer.android.com/studio)
- **Gerenciador de Dependências:** Gradle
- **API Mínima:** Android 5.0 (API 21)
- **Componentes:** ImageView, ImageButton, TextView, Button

---

## 📋 Requisitos do Projeto

### Configurações Iniciais

| Configuração | Valor |
|-------------|-------|
| Project Name | App Jokenpo |
| Package Name | br.ulbra.appjokenpo |
| Linguagem | Java |
| Minimum SDK | API 21 (Android 5.0) |
| Activity Name | MainActivity |
| Layout Name | activity_main |

### Imagens Necessárias

Adicione as seguintes imagens em `res/drawable/`:

1. **padrão.png** - Imagem padrão (exibida no início)
2. **pedra.png** - Imagem da pedra
3. **papel.png** - Imagem do papel
4. **tesoura.png** - Imagem da tesoura

**Nota:** Você pode usar imagens próprias ou baixar do Classroom

---

## 📁 Estrutura do Projeto

```
AppJokenpo/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── br/ulbra/appjokenpo/
│   │   │   │       └── MainActivity.java
│   │   │   └── res/
│   │   │       ├── layout/
│   │   │       │   └── activity_main.xml
│   │   │       └── drawable/
│   │   │           ├── padrão.png
│   │   │           ├── pedra.png
│   │   │           ├── papel.png
│   │   │           └── tesoura.png
│   └── build.gradle
└── README.md
```

---

## 📝 Código Completo

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/tvTitulo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Jokenpo"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_marginBottom="24dp" />

    <TextView
        android:id="@+id/tvEscolhaApp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Escolha do App:"
        android:textSize="16sp"
        android:layout_marginBottom="8dp" />

    <ImageView
        android:id="@+id/imgApp"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@drawable/padrão"
        android:scaleType="centerInside"
        android:layout_gravity="center_horizontal"
        android:layout_marginBottom="24dp" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Faça sua escolha!"
        android:textSize="18sp"
        android:textStyle="bold"
        android:textAlignment="center"
        android:layout_marginBottom="24dp" />

    <TextView
        android:id="@+id/txtPlacar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Você: 0 - App: 0"
        android:textSize="16sp"
        android:textAlignment="center"
        android:layout_marginBottom="32dp" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center_horizontal"
        android:layout_marginBottom="32dp">

        <Button
            android:id="@+id/btnPedra"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="PEDRA"
            android:onClick="selecionadoPedra"
            android:layout_marginEnd="8dp" />

        <Button
            android:id="@+id/btnPapel"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="PAPEL"
            android:onClick="selecionadoPapel"
            android:layout_marginEnd="8dp" />

        <Button
            android:id="@+id/btnTesoura"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="TESOURA"
            android:onClick="selecionadoTesoura" />

    </LinearLayout>

    <Button
        android:id="@+id/btnReiniciar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="REINICIAR JOGO"
        android:onClick="reiniciarJogo"
        android:padding="16dp" />

</LinearLayout>
```

### MainActivity.java

```java
package br.ulbra.appjokenpo;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;
import android.widget.TextView;
import java.util.Random;

public class MainActivity extends AppCompatActivity {

    int pontuacaoJogador = 0;
    int pontuacaoApp = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    // Métodos de seleção chamados via onClick
    public void selecionadoPedra(View view) {
        this.opcaoSelecionado("pedra");
    }

    public void selecionadoPapel(View view) {
        this.opcaoSelecionado("papel");
    }

    public void selecionadoTesoura(View view) {
        this.opcaoSelecionado("tesoura");
    }

    // Método principal que processa a jogada
    public void opcaoSelecionado(String opcaoSelecionada) {
        ImageView imageResultado = findViewById(R.id.imgApp);
        TextView txtResult = findViewById(R.id.txtResultado);

        // Gera escolha aleatória para o aplicativo
        String opcoes[] = {"pedra", "papel", "tesoura"};
        String opcaoApp = opcoes[new Random().nextInt(3)];

        // Exibe a imagem da escolha do app
        switch (opcaoApp) {
            case "pedra":
                imageResultado.setImageResource(R.drawable.pedra);
                break;
            case "papel":
                imageResultado.setImageResource(R.drawable.papel);
                break;
            case "tesoura":
                imageResultado.setImageResource(R.drawable.tesoura);
                break;
        }

        // Verifica quem ganhou
        if ((opcaoApp.equals("tesoura") && opcaoSelecionada.equals("papel")) ||
            (opcaoApp.equals("papel") && opcaoSelecionada.equals("pedra")) ||
            (opcaoApp.equals("pedra") && opcaoSelecionada.equals("tesoura"))) {
            txtResult.setText("Resultado: Você PERDEU... :(");
            pontuacaoApp++;
        } else if ((opcaoSelecionada.equals("tesoura") && opcaoApp.equals("papel")) ||
                   (opcaoSelecionada.equals("papel") && opcaoApp.equals("pedra")) ||
                   (opcaoSelecionada.equals("pedra") && opcaoApp.equals("tesoura"))) {
            txtResult.setText("Resultado: Você GANHOU... ;D");
            pontuacaoJogador++;
        } else {
            txtResult.setText("Resultado: Vocês EMPATARAM... :|");
        }

        // Atualiza o placar
        atualizarPlacar();
    }

    // Atualiza a exibição do placar
    public void atualizarPlacar() {
        TextView txtPlacar = findViewById(R.id.txtPlacar);
        txtPlacar.setText("Você: " + pontuacaoJogador + " - App: " + pontuacaoApp);
    }

    // Reinicia o jogo
    public void reiniciarJogo(View view) {
        pontuacaoJogador = 0;
        pontuacaoApp = 0;
        atualizarPlacar();
        
        TextView txtResult = findViewById(R.id.txtResultado);
        txtResult.setText("Faça sua escolha!");
        
        ImageView imageResultado = findViewById(R.id.imgApp);
        imageResultado.setImageResource(R.drawable.padrão);
    }
}
```

---

## 📚 Conceitos Principais

### Random

Gera números aleatórios para escolha do app:

```java
String opcoes[] = {"pedra", "papel", "tesoura"};
String opcaoApp = opcoes[new Random().nextInt(3)];
```

**O que faz:**
- `nextInt(3)` gera número aleatório entre 0 e 2
- Seleciona a posição correspondente no array

### Switch/Case

Executa diferentes ações baseado em valor:

```java
switch (opcaoApp) {
    case "pedra":
        imageResultado.setImageResource(R.drawable.pedra);
        break;
    case "papel":
        imageResultado.setImageResource(R.drawable.papel);
        break;
}
```

### Comparação com equals()

Compara strings em Java:

```java
if (opcaoApp.equals("tesoura") && opcaoSelecionada.equals("papel")) {
    // A escolha do app é tesoura E do jogador é papel
}
```

### onClick no XML

Define método a ser chamado ao clicar:

```xml
<Button
    android:onClick="selecionadoPedra"
    ... />
```

---

## 💡 Conceitos Aprendidos

Durante o desenvolvimento desta aplicação, aprendemos:

1. **Random** - Geração de números aleatórios
2. **Arrays** - Armazenar múltiplas opções
3. **Switch/Case** - Decisões múltiplas
4. **Operadores Lógicos** - && (E), || (OU)
5. **String.equals()** - Comparação de textos
6. **ImageView** - Exibição de imagens
7. **android:onClick** - Eventos diretos do XML
8. **Variáveis de Classe** - Persistência entre chamadas
9. **Placar Dinâmico** - Manutenção de contadores
10. **Fluxo de Lógica** - Determinação de vencedor

---

## 🚀 Como Executar

1. **Abra o Android Studio**
2. **Crie um novo projeto** chamado "App Jokenpo"
3. **Copie o layout XML** para `activity_main.xml`
4. **Copie o código Java** para `MainActivity.java`
5. **Adicione as imagens** em `res/drawable/` (pedra.png, papel.png, tesoura.png, padrão.png)
6. **Compile o projeto** - Build > Rebuild Project
7. **Execute no emulador** - Run > Run 'app'
8. **Teste o jogo:**
   - Clique em uma opção (Pedra, Papel ou Tesoura)
   - Veja a escolha do app
   - Observe o resultado
   - Acompanhe o placar
   - Clique em "Reiniciar Jogo" para resetar

---

## ✅ Resultado Final

O aplicativo apresentará:

✅ Três botões para seleção do jogador  
✅ Imagem que exibe escolha do app  
✅ Mensagem de resultado da rodada  
✅ Placar dinâmico e atualizado  
✅ Botão para reiniciar o jogo  
✅ Lógica correta de vencedor/perdedor/empate  
✅ Interface responsiva e intuitiva  

---

## 🎓 Exemplos de Rodadas

### Rodada 1: Jogador Vence
```
Jogador escolhe: PEDRA
App escolhe: TESOURA
Resultado: "Você GANHOU... ;D"
Placar: Você: 1 - App: 0
```

### Rodada 2: App Vence
```
Jogador escolhe: PAPEL
App escolhe: TESOURA
Resultado: "Você PERDEU... :("
Placar: Você: 1 - App: 1
```

### Rodada 3: Empate
```
Jogador escolhe: PEDRA
App escolhe: PEDRA
Resultado: "Vocês EMPATARAM... :|"
Placar: Você: 1 - App: 1
```

---

## 🔧 Desafios Propostos

### Desafio 1: Estatísticas Detalhadas ⭐

Adicione um TextView para mostrar:
- Total de vitórias
- Total de derrotas
- Total de empates
- Percentual de vitória

```java
int totalVitorias = pontuacaoJogador;
int totalDerrotas = pontuacaoApp;
int totalRodadas = totalVitorias + totalDerrotas;
int percentual = (totalVitorias * 100) / totalRodadas;
```

### Desafio 2: Sons e Animações ⭐⭐

- Adicionar som ao ganhar/perder
- Animação ao revelar escolha do app
- Vibração ao fim de cada rodada

### Desafio 3: Modo Melhor de 3 ⭐⭐

Implementar sistema de melhores de 3, 5 ou 7 rodadas:
- App determina quando o jogo acabou
- Exibe vencedor final
- Oferece novo jogo

### Desafio 4: Dificuldades ⭐⭐⭐

Adicionar diferentes níveis:
- **Fácil:** Aleatório puro
- **Difícil:** App tenta adivinhar sua próxima jogada
- **Extremo:** App joga o que vence sua última escolha

---

## 🎮 Estratégias de Jogo

### Padrões Comuns

- Muitos iniciantes começam com pedra
- Após perder, tendem a mudar
- Alguns repetem a mesma escolha

### Estratégias Básicas

1. **Aleatória:** Escolha ao acaso
2. **Espelho:** Repetir última escolha do oponente
3. **Contador:** Jogar o que vence a última escolha
4. **Cíclica:** Seguir sequência pedra → papel → tesoura

---

## 🔍 Diferenças na Lógica

### Verificação de Vitória

```java
// App vence se:
if ((opcaoApp.equals("tesoura") && opcaoSelecionada.equals("papel")) ||
    (opcaoApp.equals("papel") && opcaoSelecionada.equals("pedra")) ||
    (opcaoApp.equals("pedra") && opcaoSelecionada.equals("tesoura"))) {
    // App venceu
}
```

### Verificação de Derrota

```java
// Jogador vence se:
if ((opcaoSelecionada.equals("tesoura") && opcaoApp.equals("papel")) ||
    (opcaoSelecionada.equals("papel") && opcaoApp.equals("pedra")) ||
    (opcaoSelecionada.equals("pedra") && opcaoApp.equals("tesoura"))) {
    // Jogador venceu
}
```

---

## ⚠️ Possíveis Erros e Soluções

### Erro: "Method not found 'selecionadoPedra'"
- **Causa:** Método não existe em MainActivity
- **Solução:** Verificar se os métodos estão públicos e com assinatura correta

### Erro: "NullPointerException" no ImageView
- **Causa:** ID da imagem no XML não corresponde
- **Solução:** Verificar se o ID `imgApp` existe no layout

### Erro: "Imagem não aparece"
- **Causa:** Arquivo de imagem não existe em drawable
- **Solução:** Adicionar as imagens (pedra.png, papel.png, tesoura.png) em res/drawable

---

## 🔧 Melhorias Futuras

- 🎨 Adicionar Material Design
- 🎵 Efeitos sonoros
- 💾 Salvar melhor placar
- 🏆 Ranking de jogadores
- 📱 Modo multijogador local
- 🎯 Diferentes temas visuais
- ⚡ Modo rápido (rodadas cronometradas)
- 🌐 Jogar online

---

## 👨‍💻 Autor

Desenvolvido como atividade de aprendizado em Android com Java.

---

## 📝 Licença

Este projeto é fornecido como material educacional.

---

## 🤝 Contribuições

Sugestões e melhorias são bem-vindas!

**Let's Code pessoal!!!** 🚀
