---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024847"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>AddressHeaderCollection dans WCF lève maintenant une exception ArgumentException si un élément addressHeader a la valeur Null

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, le constructeur <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> lève une <xref:System.ArgumentException> si l’un des éléments a la valeur `null`. Dans .NET Framework 4.7 et versions antérieures, aucune exception n’est levée.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes de compatibilité avec cette modification sur le .NET Framework 4.7.1 ou une version ultérieure, vous pouvez choisir de l’annuler en ajoutant la ligne suivante à la `<runtime>` section du fichier app.config :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| Nom    | Valeur   |
|:--------|:--------|
| Étendue   | Secondaire   |
| Version | 4.7.1   |
| Type    | Runtime |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
