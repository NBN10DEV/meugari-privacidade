# 🚛 Meu Gari

Aplicativo Android gratuito, de desenvolvimento privado e independente, que ajuda moradores de **Florianópolis/SC** a saber **quando e onde** acontece a coleta de resíduos e **onde descartar** cada tipo de material.

!\[Versão](https://img.shields.io/badge/vers%C3%A3o-3.1.3-2E7D32)
!\[Plataforma](https://img.shields.io/badge/plataforma-Android%209%2B-3DDC84)
!\[Linguagem](https://img.shields.io/badge/Kotlin-7F52FF)
!\[Anúncios](https://img.shields.io/badge/an%C3%BAncios-nenhum-FF6D00)

> ⚠️ \*\*Aviso:\*\* o Meu Gari \*\*não é um aplicativo oficial\*\* e \*\*não representa\*\* a Prefeitura Municipal de Florianópolis, a Comcap ou qualquer entidade governamental. É um projeto privado, sem vínculo ou autorização de órgãos públicos.
>
> \*\*Fonte oficial das informações (dados públicos):\*\* \[Prefeitura Municipal de Florianópolis](https://www.pmf.sc.gov.br/servicos/index.php?pagina=servpagina\&id=260) · \[pmf.sc.gov.br](https://www.pmf.sc.gov.br/)

## Capturas de tela

!\[Tela do app](Screenshot\_1.png)
!\[Tela do app](Screenshot\_2.png)
!\[Tela do app](Screenshot\_3.png)

## Funcionalidades

O app tem cinco abas na barra inferior:

|Aba|O que faz|
|-|-|
|**Mapa**|Mapa interativo do Google com sua posição ("Você está aqui!"), busca de endereços e botão para centralizar na sua localização. Toque em uma rota ou ponto de coleta para ver horário e turno.|
|**Visualização**|Escolha a camada exibida no mapa: Coleta Convencional, Coleta Seletiva, Coleta Flex Vidros, Coleta Orgânicos ou Mapa normal.|
|**Favoritos**|Salve locais com o nome que quiser, renomeie, exclua e ative o **aviso de coleta** (sino) para receber uma notificação no dia e turno da coleta, mesmo com o app fechado.|
|**Descarte**|Encontre o ponto mais próximo para descartar vidro, isopor, recicláveis, orgânicos e entulho (PEVs e Ecopontos), veja no mapa do app ou abra a rota no Google Maps.|
|**Notícias**|Conteúdo sobre sustentabilidade de [floripasustentavel.com.br](https://floripasustentavel.com.br/).|

Outros recursos:

* Verificação automática de nova versão ao abrir o app.
* Funciona sem a permissão de localização (navegação manual e busca por endereço).
* Sem cadastro, sem login e sem anúncios.

## Privacidade

* **Política de Privacidade:** [https://nbn10dev.github.io/meugari-privacidade/](https://nbn10dev.github.io/meugari-privacidade/)
* A localização só é lida com o app aberto e **não é enviada a servidores do desenvolvedor**.
* Favoritos e lembretes ficam **apenas no aparelho** (backup em nuvem desativado).

### Permissões

|Permissão|Para que serve|
|-|-|
|`ACCESS\_FINE\_LOCATION` / `ACCESS\_COARSE\_LOCATION`|Mostrar sua posição no mapa e calcular distâncias (somente em primeiro plano).|
|`INTERNET`|Mapa, busca de endereços, verificação de atualização e aba Notícias.|
|`POST\_NOTIFICATIONS`|Exibir os avisos de coleta que você ativa.|
|`RECEIVE\_BOOT\_COMPLETED`|Reagendar seus avisos após reiniciar o aparelho.|

## Tecnologias

* **Kotlin** · Android nativo (View Binding / Data Binding)
* **Google Maps SDK for Android** e **Maps Utils** (camadas KML)
* **Google Play Services Location**
* **AlarmManager** + notificações locais para os lembretes
* **SharedPreferences** + **Gson** para favoritos e lembretes
* **Material Components**, [CurvedBottomNavigation](https://github.com/qamarelsafadi/CurvedBottomNavigation), CircleImageView

||                                  |
|-|----------------------------------|
|Pacote| `com.nbn10developer.meugari`     |
|Versão| 3.1.2 (código 11)                |
|minSdk / targetSdk| 28 (Android 9) / 36 (Android 16) |

## Como compilar

**Requisitos:** Android Studio recente, JDK 11+ e uma chave da **Maps SDK for Android** (Google Cloud Console).

1. Clone o repositório e abra a pasta no Android Studio.
2. No arquivo `local.properties` (que não deve ser versionado), adicione sua chave:

```properties
   MAPS\_API\_KEY=sua\_chave\_aqui
   ```

3. Sincronize o Gradle e execute em um dispositivo ou emulador com Google Play Services.

> ⚠️ Nunca publique sua chave de API. Restrinja-a no Google Cloud ao pacote `com.coding.meugari` e à impressão digital SHA-1 do seu certificado.

Para gerar a versão de publicação:

```bash
./gradlew bundleRelease
```

## Estrutura do projeto

```
app/src/main/
├── java/com/coding/meugari/
│   ├── MainActivity.kt              # Tela inicial
│   ├── HomeActivity.kt              # Mapa, camadas, favoritos e navegação
│   ├── DescarteFragment.kt          # Pontos de descarte (PEVs e Ecopontos)
│   ├── OptionsFragment.kt           # Aba Notícias (WebView)
│   ├── CollectionScheduler.kt       # Agendamento dos avisos de coleta
│   ├── CollectionReminderReceiver.kt# Notificações e reagendamento após boot
│   ├── UpdateChecker.kt             # Verificação de nova versão
│   └── adapters/                    # Listas de camadas e favoritos
└── res/raw/                         # Camadas KML de coleta (embutidas no app)
    ├── coleta\_convencional.kml
    ├── coleta\_seletiva.kml
    ├── coleta\_flex\_vidros.kml
    └── coleta\_flex\_organicos.kml
```

## Sobre os dados

As camadas de coleta (KML) e a lista de pontos de descarte são baseadas em **dados públicos da Prefeitura Municipal de Florianópolis** e estão **embutidas no app**; para atualizá-las é preciso publicar uma nova versão. Os horários e locais são informativos — confirme sempre com os canais oficiais da Prefeitura de Florianópolis / Comcap.

## Autores

Desenvolvido pela equipe **nbn10developer**:

* Narciso Brunazzo Neto
* Alexandre Flores Jacques
* Richard Leal Vatras
* Marília Cumaru Inhamuns

**Contato:** nbn10developer@gmail.com

## Licença

© 2026 Meu Gari — nbn10developer. Todos os direitos reservados.

