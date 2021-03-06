---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497072"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Un blocage peut se produire lors de l’utilisation de services réentrants

#### <a name="details"></a>Détails

Un blocage peut survenir dans un service réentrant, ce qui limite les instances du service à un thread d’exécution à la fois. Les services susceptibles de rencontrer ce problème ont le <xref:System.ServiceModel.ServiceBehaviorAttribute> suivant dans leur code :

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a>Suggestion

Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :

- Définissez le mode d’accès concurrentiel du service sur <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> . Par exemple :

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework. Cela désactive le flux de l’<xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

La valeur de `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` ne doit jamais être définie sur `false` pour les services réentrants.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
