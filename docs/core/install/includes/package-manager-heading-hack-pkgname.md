---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77466081"
---

Les paquets ajoutés aux flux de gestionnaire de `{product}-{type}-{version}`paquets sont nommés dans un format hackable: .

- **Produit**\
Le type de produit .NET à installer. Les options valides sont les suivantes :

  - dotnet
  - aspnetcore

- **Type**\
Choisit le SDK ou l’heure d’exécution. Les options valides sont les suivantes :

  - SDK
  - runtime

- **Version**\
La version du SDK ou l’heure d’exécution à installer. Cet article donnera toujours les instructions pour la dernière version prise en charge. Les options valides sont n’importe quelle version libérée, telles que :

  - 3.1
  - 3.0
  - 2.1

  Il est possible que le SDK/runtime que vous essayez de télécharger n’est pas disponible pour votre distribution Linux. Pour une liste de distributions prises en charge, voir [.NET Core dépendances et exigences](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Exemples

- Installer le ASP.NET cœur 3.1 temps d’exécution:`aspnetcore-runtime-3.1`
- Installer le temps d’exécution .NET Core 2.1 :`dotnet-runtime-2.1`
- Installer le .NET Core 3.0 SDK:`dotnet-sdk-3.0`

### <a name="package-missing"></a>Paquet manquant

Si la combinaison de versions de paquet ne fonctionne pas, elle n’est pas disponible. Par exemple, il n’y a pas de ASP.NET Core SDK, les composants SDK sont inclus avec le SDK core .NET. La `aspnetcore-sdk-2.2` valeur est incorrecte et doit être `dotnet-sdk-2.2`. Pour une liste de distributions Linux prises en charge par .NET Core, voir [.NET Core dépendances et exigences](../dependencies.md?pivots=os-linux).
