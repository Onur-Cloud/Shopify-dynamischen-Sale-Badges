# Dynamisches Sale-Badge für Shopify

Dieses Repository enthält die Anleitung zur Integration eines dynamischen Sale-Badges in Ihr Shopify-Theme.

## Vorschau

![Vorschau 1](https://i.ibb.co/1XsSZNc/Bildschirmfoto-11-9-2024-1485-bluessenz-de.jpg)
![Vorschau 2](https://i.ibb.co/Lt3V4B3/Bildschirmfoto-11-9-2024-14835-bluessenz-de.jpg)

## Integration

### 1. Erstellen Sie ein neues Snippet

- Erstellen Sie eine neue Datei `snippets/dynamic-sale-badge.liquid` in Ihrem Shopify-Theme.
- Fügen Sie den Code für das dynamische Sale-Badge ein (siehe separate Liquid-Datei im Repository).

### 2. Ersetzen Sie den bestehenden Sale-Badge-Code

Suchen Sie in Ihrer Theme-Datei (normalerweise `snippets/card-product.liquid`) den folgenden Code-Block:

```liquid
<div class="card__badge {{ settings.badge_position }}">
  {%- if card_product.available == false -%}
    <span
      id="Badge-{{ section_id }}-{{ card_product.id }}"
      class="badge badge--bottom-left color-{{ settings.sold_out_badge_color_scheme }}"
    >
      {{- 'products.product.sold_out' | t -}}
    </span>
  {%- elsif card_product.compare_at_price > card_product.price and card_product.available -%}
    <span
      id="Badge-{{ section_id }}-{{ card_product.id }}"
      class="badge badge--bottom-left color-{{ settings.sale_badge_color_scheme }}"
    >
      {{- 'products.product.on_sale' | t -}}
    </span>
  {%- endif -%}
</div>
```

### 3. Fügen Sie das neue dynamische Sale-Badge ein

Ersetzen Sie den gesamten `<div class="card__badge">` Block durch:

```liquid
{% render 'dynamic-sale-badge', product: card_product %}
```

### 4. Überprüfen Sie die Änderungen

Speichern Sie die Änderungen und überprüfen Sie Ihr Theme. Das neue dynamische Sale-Badge sollte nun auf Ihren Produktkarten erscheinen, wenn ein Produkt im Angebot ist.

## Anpassungen

Sie können das Aussehen des Badges anpassen, indem Sie den CSS-Code in der `dynamic-sale-badge.liquid` Datei bearbeiten.

## Unterstützung

Bei Fragen oder Problemen öffnen Sie bitte ein Issue in diesem Repository.
