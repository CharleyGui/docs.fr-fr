---
title: 'Comment : référencer un assembly avec nom fort'
description: Cet article explique comment référencer des types ou des ressources dans un assembly .NET avec nom fort, au moment de la compilation ou de l’exécution.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 919e4f4cf467e8fc28c3d007963393dad134ab57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724050"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Comment : référencer un assembly avec nom fort

Le référencement de types ou de ressources dans un assembly avec nom fort est généralement un processus transparent. Vous pouvez effectuer la référence au moment de la compilation (liaison anticipée) ou au moment de l’exécution.  
  
Une référence au moment de la compilation se produit lorsque vous indiquez au compilateur que l’assembly à compiler fait explicitement référence à un autre assembly. Quand vous utilisez le référencement au moment de la compilation, le compilateur obtient automatiquement la clé publique de l’assembly avec nom fort ciblé et la place dans la référence d’assembly de l’assembly compilé.
  
> [!NOTE]
> Un assembly avec nom fort peut uniquement utiliser les types d'autres assemblys avec nom fort. Si ce n'était pas le cas, la sécurité de l'assembly avec nom fort serait compromise.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Créer une référence au moment de la compilation à un assembly avec nom fort  

Saisissez ensuite la commande suivante dans une invite de commandes :  

\<*compiler command*>**/Reference :**\<*assembly name*>  

Dans cette commande, *commande_compilateur* est la commande du compilateur pour le langage que vous utilisez, et *nom_assembly* est le nom de l’assembly avec nom fort référencé. Vous pouvez également utiliser d’autres options du compilateur, telles que **/t:library**, qui permet de créer un assembly de bibliothèque.  

L’exemple suivant crée un assembly appelé *myAssembly.dll* qui référence un assembly avec nom fort appelé *myLibAssembly.dll* à partir d’un module de code appelé *myAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Effectuer une référence au moment de l’exécution à un assembly avec nom fort  
  
Quand vous faites référence à un assembly avec nom fort, par exemple à l’aide de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> méthode ou <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , vous devez utiliser le nom complet de l’assembly avec nom fort référencé. La syntaxe d’un nom complet est la suivante :  

\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*>  

Par exemple :  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

Dans cet exemple, `PublicKeyToken` est la forme hexadécimale du jeton de clé publique. S’il n’existe aucune valeur de culture, utilisez `Culture=neutral`.  

L’exemple de code suivant montre comment utiliser ces informations avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

Vous pouvez imprimer le format hexadécimal de la clé publique et du jeton de clé publique pour un assembly spécifique en utilisant la commande [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) suivante :  

**SN-TP \<** *assembly* **>**  

Si vous avez un fichier de clé publique, vous pouvez utiliser la commande suivante (notez la différence de casse de l’option de ligne de commande) à la place :  

**SN-TP \<** *public key file* **>**  

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
