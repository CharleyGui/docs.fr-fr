---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466081"
---

Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}`.

- \ du **produit**
Type de produit .NET à installer. Les options valides sont les suivantes :

  - dotnet
  - aspnetcore

- \ de **type**
Choisit le kit de développement logiciel (SDK) ou le Runtime. Les options valides sont les suivantes :

  - SDK
  - runtime

- \ de **version**
Version du kit de développement logiciel (SDK) ou du runtime à installer. Cet article fournira toujours les instructions relatives à la dernière version prise en charge. Les options valides sont toutes les versions publiées, par exemple :

  - 3.1
  - 3.0
  - 2.1

  Il est possible que le kit de développement logiciel (SDK)/Runtime que vous essayez de télécharger ne soit pas disponible pour votre distribution Linux. Pour obtenir la liste des distributions prises en charge, consultez [dépendances et exigences de .net Core](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Exemples

- Installer le ASP.NET Core 3,1 Runtime : `aspnetcore-runtime-3.1`
- Installer le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`
- Installez le kit de développement logiciel (SDK) .NET Core 3,0 : `dotnet-sdk-3.0`

### <a name="package-missing"></a>Package manquant

Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible. Par exemple, il n’existe pas de ASP.NET Core SDK, les composants du kit de développement logiciel (SDK) sont inclus dans le kit SDK .NET Core. La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2`. Pour obtenir la liste des distributions Linux prises en charge par .NET Core, consultez [dépendances et exigences de .net Core](../dependencies.md?pivots=os-linux).
