# JogodaForca_Portugol
programa {
  inclua biblioteca Texto --> txt

  // declarações globais
  cadeia palavra, continuar, letra, vetorDaPalavra[100], letras[26]
  inteiro opcao, tentativas = 7, numChar, contLetra = 0, contAcertos = 0
  logico achouLetra = falso

  funcao inicio() {
    faca {
      escreva(":: JOGO DA FORCA ::\n\n")
      escreva("1 - Iniciar o jogo\n")
      escreva("0 - Sair do jogo\n")
      leia(opcao)

      escolha(opcao) {
        caso 1:
          iniciar()
        pare
      }
    } enquanto(opcao != 0)
  }

  funcao iniciar() {
    limpa()
    escreva(":: JOGO DA FORCA ::\n\n")
    escreva("Para começar, digite uma palavra: \n")
    leia(palavra)

    limpa()
    escreva("Ótimo! sua palavra foi definida.\n")
    escreva("\n\nPresione 'enter' para continuar")
    leia(continuar)

    novaLetra()
  }

  funcao novaLetra() {
    escreva("\n\n")
    listarPalavra()

    enquanto(tentativas >= 0) {
      limpa()
      escreva(":: JOGO DA FORCA ::\n\n")
      escreva("\nA palavra possui ", numChar, " letras \n\n")
      listarPalavra()
      montarBoneco()

      se(tentativas == 100){
        escreva("\n\nVocê acertou!\n\n")
        escreva("Digite 'enter' para recomeçar")
        leia(continuar)
        iniciar()
      } senao {
        escreva("\n\nVocê tem ", tentativas, " tentativas.\n\n")
        escreva("Digite uma letra: ")
        leia(letra)
        atualizarTentativas(letra)
        contLetra++
      }
    }
  }

  funcao atualizarTentativas(cadeia letra){
    escreva(":: JOGO DA FORCA ::\n\n")
    escreva("\nA palavra possui ", numChar, "letras: \n\n")

    para(inteiro i = 0; i < numChar; i++){
      se(txt.obter_caracter(palavra, i) == letra){
        vetorDaPalavra[i] = letra + " "
        achouLetra = verdadeiro
        contAcertos++
        se(contAcertos == numChar){
          tentativas = 100
        }
      }
      escreva(vetorDaPalavra[i])
    }

    se(achouLetra == falso){
      tentativas--
    }

    achouLetra = falso
  }

  funcao listarTentativas(){
    para(inteiro i = 0; numChar; i++){
      escreva(vetorDaPalavra[i], " ")
    }
  se(contLetra > 0){
  letras[contLetra] = letra
  escreva("\n_______________\n")
  escreva("Letras digitadas: ", contLetra, "\n\n")
  para(inteiro i = 1; i <= contLetra; i++){
    escreva(letras[i], " | ")
    }
    escreva("\n_______________\n")
  }
}
  funcao listarPalavra() {
    numChar = txt.numero_caracteres(palavra)

    para(inteiro i = 0; i < numChar; i++) {
      vetorDaPalavra[i] = "_ "
      escreva(vetorDaPalavra[i])
    }
  }

  funcao montarBoneco() {
    escreva("\n\n")
    se(tentativas == 100) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|      Õ\n")
      escreva("|     L|/\n")
      escreva("|_____/ L___\n")
    }
    se(tentativas == 7){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|      Õ\n")
      escreva("|     L|/\n")
      escreva("|_____/ L___\n")
    }
    se(tentativas == 6){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|       \n")
      escreva("|       \n")
      escreva("|       \n")
      escreva("|       \n")
    }
    se(tentativas == 5){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|      |\n")
      escreva("|       \n")
      escreva("|       \n")
      escreva("|       \n")
    }
    se(tentativas == 4){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|\n")
      escreva("|       \n")
      escreva("|       \n")
      escreva("|       \n")
    }
     se(tentativas == 3){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|       \n")
      escreva("|       \n")
      escreva("|       \n")
    }
     se(tentativas == 2){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|     / \n")
      escreva("|       \n")
      escreva("|       \n")
    }
     se(tentativas == 1){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|     / L \n")
      escreva("|       \n")
      escreva("|       \n")
    }
    se(tentativas == 0){
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|     --|--\n")
      escreva("| __Õ__/ L__\n")
    }
  }
}
