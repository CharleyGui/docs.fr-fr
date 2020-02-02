---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920668"
---

Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}`.

- \ du **produit**
Type de produit .NET à installer. Les options admises sont les suivantes :

  - dotnet
  - aspnetcore

- **type**\
Choisit le kit de développement logiciel (SDK) ou le Runtime. Les options admises sont les suivantes :

  - sdk
  - Runtime

- \ de **version**
Version du kit de développement logiciel (SDK) ou du runtime à installer. Cet article fournira toujours les instructions relatives à la dernière version prise en charge. Les options valides sont toutes les versions publiées, par exemple :

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>Exemples

- Installez le kit de développement logiciel (SDK) .NET Core 2,2 : `dotnet-sdk-2.2`
- Installer le ASP.NET Core 3,1 Runtime : `aspnetcore-runtime-3.1`
- Installer le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`

### <a name="package-missing"></a>Package manquant

Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible. Par exemple, il n’existe pas de ASP.NET Core SDK, les composants du kit de développement logiciel (SDK) sont inclus dans le kit SDK .NET Core. La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2`.
