---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616246"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Les sommes de contrôle XAML de workflow pour les symboles passent de SHA1 à SHA256

#### <a name="details"></a>Détails

Pour prendre en charge le débogage avec Visual Studio, l’exécution du workflow génère une somme de contrôle pour un fichier XAML de workflow à l’aide d’un algorithme de hachage. Dans .NET Framework 4.6.2 et les versions antérieures, le hachage de somme de contrôle de flux de travail utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À compter de .NET Framework 4.7, l’algorithme par défaut est passé à SHA1. À compter de .NET Framework 4.8, l’algorithme par défaut est passé à SHA256.

#### <a name="suggestion"></a>Suggestion

Si votre code n’est pas en mesure de charger des instances de workflow ou de rechercher les symboles appropriés en raison d’une erreur de somme de contrôle, essayez de définir le `AppContext` commutateur «Switch.SysTEM. Activities. UseSHA1HashForDebuggerSymbols» en `true` . Dans le code :

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

Ou dans la configuration :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.8         |
| Type    | Reciblage |
