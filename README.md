# Chamado Rápido — Engenharia Clínica — iPhone 6 Plus

Versão do aplicativo preparada para o **iPhone 6 Plus com iOS 12.5.7**. O usuário lê o QR Code do equipamento, confirma a falha, responde à triagem de segurança e abre o WhatsApp com a mensagem pronta.

## Recursos

- leitura de QR Code pela câmera ou por uma foto;
- busca por patrimônio, série ou código;
- preenchimento dos dados do equipamento;
- triagem de evento adverso, incidente sem dano, quase falha, condição de risco ou queixa técnica;
- orientação inicial sobre registro no SIGQuali;
- mensagem pronta para o WhatsApp `(84) 99447-2995`;
- base local de equipamentos, com funcionamento offline após o primeiro carregamento da versão web;
- layout e JavaScript adaptados para o navegador antigo do iOS 12.

## Compatibilidade escolhida

- destino mínimo: iOS 12.0;
- aparelho: iPhone 6 Plus;
- Cordova iOS: 7.1.1;
- geração: GitHub Actions em macOS;
- versão web instalável: GitHub Pages.

O Cordova iOS 8 não foi usado porque exige iOS 13 ou superior. O iPhone 6 Plus permanece no iOS 12.

Antes de publicar a base real de equipamentos no GitHub Pages, confirme a política institucional: dependendo da conta e do repositório, a página pode ficar acessível publicamente.

## Onde estão as imagens

- `resources/icon.png` e `resources/splash.png`: arquivos principais;
- `resources/ios/`: todos os tamanhos de ícone e abertura exigidos pelo iPhone;
- `www/img/`: ícones usados quando o aplicativo é instalado pelo Safari.

## Estrutura

- `www/index.html`: aplicativo;
- `www/equipamentos.json`: base local de equipamentos;
- `www/manifest.webmanifest` e `www/service-worker.js`: instalação pelo Safari e modo offline;
- `config.xml`: configuração do iPhone, câmera e iOS 12;
- `package.json`: dependências;
- `.github/workflows/gerar-ipa-nao-assinado.yml`: gera um IPA sem assinatura;
- `.github/workflows/publicar-webapp-iphone.yml`: publica a versão instalável pelo Safari;
- `GERAR-E-INSTALAR-NO-IPHONE.md`: instruções completas;
- `saida/`: resultado da geração.

## Atualizar os equipamentos

Edite `www/equipamentos.json`. Cada equipamento segue este modelo:

```json
{
  "id": "008528",
  "patrimonio": "008528",
  "nome": "Cardioversor",
  "marca": "Instramed",
  "modelo": "CardiMax",
  "serie": "092020 CM16039",
  "setor": "Urgência",
  "criticidade": "Alta"
}
```

O QR Code pode conter somente o patrimônio, uma URL com `?patrimonio=008528` ou um objeto JSON com os dados do equipamento.

## Importante sobre o IPA

O GitHub consegue compilar o arquivo, mas a Apple exige assinatura para instalar um IPA em um iPhone físico. Por isso, o fluxo automático identifica claramente o resultado como `NAO_ASSINADO`. Consulte `GERAR-E-INSTALAR-NO-IPHONE.md` antes de tentar instalar.

## Segurança

A triagem é um apoio inicial. A classificação final e a decisão sobre SIGQuali ou comunicação externa devem ser realizadas pela Engenharia Clínica em conjunto com o NSP/Gerência de Risco.
