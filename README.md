[![Support Palestine](https://raw.githubusercontent.com/Safouene1/support-palestine-banner/master/banner-support.svg)](https://github.com/Safouene1/support-palestine-banner/blob/master/Markdown-pages/Support.md)

![GitHub package.json version](https://img.shields.io/github/package-json/v/mustafagenc/kurlar) ![NPM Version](https://img.shields.io/npm/v/%40mustafagenc%2Fkurlar) ![CodeFactor Grade](https://img.shields.io/codefactor/grade/github/mustafagenc/kurlar) ![GitHub Repo stars](https://img.shields.io/github/stars/mustafagenc/kurlar)


# Kurlar

Türkiye Cumhuriyet Merkez Bankası (TCMB) tarafından yayınlanan döviz kurlarını kolayca çekmenizi sağlayan bir TypeScript kütüphanesi.

## Özellikler

- TCMB'nin günlük döviz kurlarını çekme
- Tarihe göre döviz kuru sorgulama
- JSON formatında sonuç döndürme
- TypeScript desteği ile güçlü tip kontrolü

## Kurulum

Projeyi kullanmaya başlamak için aşağıdaki adımları izleyin:

```bash
yarn add @mustafagenc/kurlar
```

## Kullanım

Aşağıdaki örnek, kütüphanenin nasıl kullanılacağını göstermektedir:

```ts
import { fetchCurrency } from "kurlar";

(async () => {
  const result = await fetchCurrency({
    currency: "USD",
    date: new Date("2023-10-26"),
  });

  console.log(result);
})();
```
```ts
import { fetchAllCurrencies } from "kurlar";

(async () => {
  try {
    const allCurrencies = await fetchAllCurrencies(new Date("2023-10-26"));

    if (allCurrencies) {
      console.log("Tüm döviz kurları:", allCurrencies);
    } else {
      console.log("Belirtilen tarihte döviz kurları bulunamadı.");
    }
  } catch (error) {
    console.error("Döviz kurları alınırken bir hata oluştu:", error);
  }
})();
```

### Döviz Kodu Listesi

`USD`, `AUD`, `DKK`, `EUR`, `GBP`, `CHF`, `SEK`, `CAD`, `KWD`, `NOK`, `SAR`, `JPY`, `BGN`, `RON`, `RUB`, `CNY`, `PKR`, `QAR`, `KRW`, `AZN`, `AED`

## API

### `fetchCurrency({ currency, date }): Promise<TCMBResponseType | null>`

- **`currency`**: Döviz kodu (ör. `"USD"`, `"EUR"`)
- **`date`**: Tarih (opsiyonel, belirtilmezse bugünün tarihi kullanılır)

Dönen değer, aşağıdaki yapıya sahiptir:

```ts
type TCMBResponseType = {
  Unit: number;
  CurrencyName: string;
  CurrencyCode: string;
  ForexBuying: number;
  ForexSelling: number;
  BanknoteBuying: number;
  BanknoteSelling: number;
};
```

## Testler

Testleri çalıştırmak için:

```bash
yarn test
```

Kod kapsamını görmek için:

```bash
yarn test:coverage
```

## Katkıda Bulunma

Katkıda bulunmak isterseniz, lütfen bir pull request gönderin veya bir issue açın.

## Lisans

Bu proje [MIT](LICENSE) ile lisanslanmıştır.
