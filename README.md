# Математика в клітинку

Дитяча гра для тренування додавання, віднімання, множення і ділення.
Застосунок для iPhone і iPad, працює без інтернету.

- Назва під значком на iPhone: **Математика**
- Назва в App Store: **Математика в клітинку**
- Bundle ID: `ua.garaschenko.matematyka`

## Що в папці

| Файл | Навіщо |
|---|---|
| `www/index.html` | сама гра |
| `resources/icon.png` | значок 1024×1024 |
| `capacitor.config.json` | налаштування застосунку |
| `codemagic.yaml` | рецепт збирання на Mac-сервері Codemagic |
| `package.json` | список потрібних бібліотек |

## Як зібрати без Mac

1. **Apple Developer**: дочекатися листа, що членство активне.
2. **Bundle ID**: developer.apple.com → Certificates, Identifiers & Profiles → Identifiers → «+» → App IDs → App → Explicit, `ua.garaschenko.matematyka`.
3. **App Store Connect**: appstoreconnect.apple.com → Apps → «+» → New App. Платформа iOS, назва «Математика в клітинку», мова Ukrainian, Bundle ID з кроку 2, SKU `matematyka1`.
4. **API-ключ**: App Store Connect → Users and Access → Integrations → App Store Connect API → «+», роль App Manager. Завантажити файл `.p8` (дається лише один раз!) і записати Issuer ID та Key ID.
5. **Codemagic**: codemagic.io → увійти через GitHub → додати цей репозиторій.
   - Team settings → Integrations → Developer Portal → додати ключ з кроку 4 під назвою `AppStoreKey`.
   - Team settings → Code signing identities → iOS certificates → Generate certificate (тип Apple Distribution).
   - Там само → iOS provisioning profiles → Fetch profiles (або створити App Store профіль для `ua.garaschenko.matematyka`).
6. **Запустити збирання**: Start new build → workflow «Математика в клітинку → TestFlight».
7. **TestFlight**: встановити програму TestFlight на iPhone, у App Store Connect → TestFlight додати себе як внутрішнього тестувальника.
