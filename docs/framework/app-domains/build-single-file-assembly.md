---
title: 'Comment : générer un assembly à fichier unique .NET Framework'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644299"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Comment : générer un assembly à fichier unique .NET Framework

Un assembly à fichier unique, qui est le type d’assembly le plus simple, contient l’implémentation et les informations de type, ainsi que le [manifeste d’assembly](../../standard/assembly/manifest.md). Vous pouvez utiliser des compilateurs de ligne de commande ou Visual Studio pour créer un assembly à fichier unique qui cible le .NET Framework. Par défaut, le compilateur crée un fichier d’assembly avec une extension *. exe* .

> [!NOTE]
> Visual Studio pour C# et Visual Basic peut être utilisé uniquement pour créer des assemblys à fichier unique. Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual C++.

Les procédures suivantes montrent comment créer des assemblys à fichier unique à l’aide des compilateurs de ligne de commande.

## <a name="create-an-assembly-with-an-exe-extension"></a>Créer un assembly avec une extension. exe

Saisissez ensuite la commande suivante dans l’invite de commandes :

\<*nom du*> \<*module* de commande du compilateur>

Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.

L’exemple suivant crée un assembly nommé *myCode. exe* à partir d’un `myCode`module de code appelé.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Créer un assembly avec une extension. exe et spécifier le nom du fichier de sortie

Saisissez ensuite la commande suivante dans l’invite de commandes :

\<*commande*> du compilateur **/out :**\<nom de*fichier*> \<nom du*module*>

Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, *nom_du_fichier* est le nom du fichier de sortie, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.

L’exemple suivant crée un assembly nommé *myAssembly. exe* à partir d’un `myCode`module de code appelé.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Créer des assemblys de bibliothèque
 Un assembly de bibliothèque est similaire à une bibliothèque de classes. Il contient des types qui seront référencés par d’autres assemblys, mais n’a aucun point d’entrée pour commencer l’exécution.

Pour créer un assembly de bibliothèque, à l’invite de commandes, tapez la commande suivante :

\<*commande*> du compilateur **-** \< *nom du module* t :Library>

Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly. Vous pouvez également utiliser d’autres options du compilateur, telles que l’option **-out:**.

L’exemple suivant crée un assembly de bibliothèque nommé *myCodeAssembly. dll* à partir d' `myCode`un module de code appelé.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Voir aussi

- [Créer des assemblys](../../standard/assembly/create.md)
- [Assemblys multifichiers](multifile-assemblies.md)
- [Comment : générer un assembly multifichier](build-multifile-assembly.md)
- [Programmer avec des assemblys](../../standard/assembly/index.md)
