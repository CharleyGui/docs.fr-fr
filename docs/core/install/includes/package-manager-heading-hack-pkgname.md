---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506861"
---

Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}` .

- **production**\
Type de produit .NET à installer. Les options valides sont les suivantes :

  - dotnet
  - aspnetcore

- **entrer**\
Choisit le kit de développement logiciel (SDK) ou le Runtime. Les options valides sont les suivantes :

  - SDK
  - runtime

- **Version**\
Version du kit de développement logiciel (SDK) ou du runtime à installer. Cet article fournira toujours les instructions relatives à la dernière version prise en charge. Les options valides sont toutes les versions publiées, par exemple :

  - 5.0
  - 3.1
  - 3.0
  - 2.1

  Il est possible que le kit de développement logiciel (SDK)/Runtime que vous essayez de télécharger ne soit pas disponible pour votre distribution Linux. Pour obtenir la liste des distributions prises en charge, consultez [dépendances et exigences de .net Core](../linux.md).

### <a name="examples"></a>Exemples

- Installez le ASP.NET Core 5,0 Runtime : `aspnetcore-runtime-5.0`
- Installez le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`
- Installez le kit de développement logiciel (SDK) .NET 5,0 : `dotnet-sdk-5.0`
- Installez le kit de développement logiciel (SDK) .NET Core 3,1 : `dotnet-sdk-3.1`

### <a name="package-missing"></a>Package manquant

Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible. Par exemple, il n’existe pas de kit de développement logiciel (SDK) ASP.NET Core, les composants SDK sont inclus dans le kit de développement logiciel (SDK) .NET. La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2` . Pour obtenir la liste des distributions Linux prises en charge par .NET Core, consultez [dépendances et exigences .net](../linux.md).
