# Gerar e instalar no iPhone 6 Plus

## Opção recomendada: instalar pelo Safari

Essa opção não exige certificado Apple e mantém o ícone na tela inicial:

1. Crie um repositório no GitHub e envie todo o conteúdo desta pasta.
2. Em **Settings > Pages**, selecione **GitHub Actions** como origem.
3. Em **Actions**, execute **Publicar aplicativo instalável pelo Safari**.
4. Abra no Safari do iPhone a URL mostrada ao final da execução.
5. Toque em **Compartilhar > Adicionar à Tela de Início**.
6. Abra pelo novo ícone `Chamado EC`.

Na primeira abertura é necessária internet. Depois disso, a estrutura principal e a base de equipamentos ficam armazenadas no aparelho. O WhatsApp continua precisando de conexão para enviar o chamado.

**Privacidade:** dependendo do tipo de conta/repositório, uma página do GitHub Pages pode ficar pública. Use apenas os equipamentos de demonstração até a instituição autorizar a publicação da base real, ou utilize uma hospedagem privada.

## Gerar o IPA pelo GitHub

1. Abra **Actions**.
2. Execute **Gerar IPA iPhone 6 Plus - não assinado**.
3. O resultado ficará nos artefatos da execução e em:
   `saida/Chamado_Rapido_EC_iPhone6Plus_NAO_ASSINADO.ipa`.

Esse IPA serve como compilação-base. Ele **não instala diretamente** em um iPhone comum porque ainda não possui a assinatura exigida pela Apple.

## Para instalar como aplicativo nativo

É necessário um destes caminhos:

- abrir o projeto em um Mac com Xcode, conectar o iPhone e selecionar sua conta Apple em **Signing & Capabilities**; ou
- configurar no GitHub um certificado Apple e um perfil de provisionamento que inclua o identificador do aparelho; ou
- distribuir uma versão assinada pelo Apple Developer, conforme as regras da Apple.

O identificador desta versão é:

`com.curiosidadesenclinica.chamadorapidoios12`

O exemplo `build.json.example` mostra os campos usados na assinatura. Nunca publique certificados, senhas, arquivos `.p12` ou perfis `.mobileprovision` dentro do repositório.

## Motivo da versão especial

O iPhone 6 Plus recebe o iOS 12.5.7. O projeto foi fixado no Cordova iOS 7.1.1 e no destino iOS 12.0 porque o Cordova iOS 8 exige iOS 13 ou superior.

Referências oficiais:

- Apple: https://support.apple.com/en-us/103015
- Cordova iOS: https://cordova.apache.org/docs/en/latest/guide/platforms/ios/
- Assinatura no Cordova: https://cordova.apache.org/docs/en/latest/guide/platforms/ios/#signing-an-app
