---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450883"
---

Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}`.

- \ du **produit**
Type de produit .NET à installer. Les options admises sont les suivantes :

  - dotnet
  - aspnetcore

- \ de **type**
Choisit le kit de développement logiciel (SDK) ou le Runtime. Les options admises sont les suivantes :

  - sdk
  - runtime

- \ de **version**
Version du kit de développement logiciel (SDK) ou du runtime à installer. Cet article fournira toujours les instructions relatives à la dernière version prise en charge. Les options valides sont toutes les versions publiées, par exemple :

  - 3,0
  - 2.2
  - 2.1

### <a name="examples"></a>Exemples

- Installez le kit de développement logiciel (SDK) .NET Core 2,2 : `dotnet-sdk-2.2`
- Installer le ASP.NET Core 3,0 Runtime : `aspnetcore-runtime-3.0`
- Installer le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`

### <a name="troubleshoot"></a>Dépannage

Si la combinaison de packages ne fonctionne pas, elle n’est pas disponible. Par exemple, il n’existe pas de ASP.NET Core SDK, les composants du kit de développement logiciel (SDK) sont inclus dans le kit SDK .NET Core. La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2`
