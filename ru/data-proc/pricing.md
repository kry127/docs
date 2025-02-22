---
editable: false
---

# Правила тарификации для {{ dataproc-name }}

{% include [currency-choice](../_includes/pricing/currency-choice.md) %}

## Из чего складывается стоимость использования {{ dataproc-name }} {#rules}

Итоговый расчет стоимости использования {{ dataproc-name }} учитывает:

* использование вычислительных ресурсов виртуальных машин {{ compute-full-name }} для развертывания хостов;
* наценку на вычислительные ресурсы за использование управляемого сервиса {{ dataproc-name }};
* использование сетевых дисков {{ compute-name }};
* использование сервиса {{ cloud-logging-full-name }} для получения и хранения логов;
* объем исходящего трафика.

{% include [pricing-gb-size](../_includes/pricing-gb-size.md) %}

### Использование вычислительных ресурсов {#rules-compute}

Стоимость начисляется за каждый час работы виртуальной машины хоста в рамках сервиса {{ compute-name }} согласно [ценам за вычислительные ресурсы {{ compute-full-name }}](../compute/pricing.md#prices), с наценкой за использование управляемого сервиса {{ dataproc-name }}.

### Использование дискового пространства {#rules-storage}

Объем хранилища, запрошенный для каждого из хостов кластера, тарифицируется в рамках сервиса {{ compute-name }} согласно [ценам на дисковое пространство](../compute/pricing.md#prices-storage).

### Использование сервиса {{ cloud-logging-full-name }} {#rules-logs}

Получение и хранение логов оплачивается по [правилам тарификации](../logging/pricing.md) сервиса {{ cloud-logging-full-name }}.


### Пример вычисления цены {#price-calculation-example}

{% list tabs %}

- Стандартные хосты

    Вы создаете кластер с одним Data-подкластером. Хост-мастер — `s2.micro` (2 vCPU, 8 ГБ RAM) с хранилищем 15 ГБ SSD, в подкластере один хост — `s2.small` (4 vCPU, 16 ГБ RAM), с хранилищем 100 ГБ HDD.

    Цены на использование ресурсов:

    * использование одного ядра прерываемой ВМ на платформе Intel Cascade Lake с 100% vCPU — 0,2040 ₽ в час;
    * использование 1 ГБ RAM прерываемой ВМ на платформе Intel Cascade Lake — 0,0492 ₽ в час;
    * использование 1 ГБ памяти диска SSD — 7,4441 ₽ в месяц;
    * использование 1 ГБ памяти диска HDD — 2,0847 ₽ в месяц.

    В таком случае цена часа использования кластера будет складываться следующим образом:

    * (2 + 4) × 0,2040 ₽ + (8 + 16) × 0,0492 ₽ = 2,4048 ₽ (за вычислительные ресурсы {{ compute-name }});
    * 2,4048 ₽ × 0.1 = 0,2405 ₽ (наценка за использование {{ dataproc-name }});
    * (15 × 7,4441 ₽ + 100 × 2,0847 ₽) / 30 / 24 = 0.4447 ₽ (за использование дисков {{ compute-name }}).

    Суммарная цена за час: 2,4048 ₽ + 0,2405 ₽ + 0,4447 ₽ = 3,09 ₽

{% endlist %}

## Цены {#prices}

### Вычислительные ресурсы хостов {#prices-hosts}


{% include [rub.md](../_pricing/data-proc/rub.md) %}



{% note info %}

Возможность использовать GPU на хостах {{ dataproc-name }} предоставляется по запросу в [службу технической поддержки]({{ link-console-support }}).

{% endnote %}

### Исходящий трафик {#prices-traffic}


{% include notitle [rub-egress-traffic.md](../_pricing/rub-egress-traffic.md) %}


