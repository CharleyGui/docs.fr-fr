---
title: 'Procédure : générer un assembly multifichier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040854"
---
# <a name="how-to-build-a-multifile-assembly"></a>Procédure : générer un assembly multifichier

Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.

> [!NOTE]
> L'IDE de Visual Studio pour C# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique. Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C++.

### <a name="to-create-a-multifile-assembly"></a>Pour créer un assembly multifichier

01. Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code. L'extension par défaut pour les modules de code est .netmodule.

    Par exemple, supposons que le fichier `Stringer` a un espace de noms appelé `myStringer`, qui inclut une classe appelée `Stringer`. La classe `Stringer` contient une méthode appelée `StringerMethod` qui écrit une seule ligne dans la console.

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    Utilisez la commande suivante pour compiler ce code :

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    La spécification du paramètre *module* à l’aide de l’option du compilateur **/t:** indique que le fichier doit être compilé comme module et non comme assembly. Le compilateur produit un module appelé `Stringer.netmodule`, qui peut être ajouté à un assembly.

02. Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code. Cette étape utilise l’option du compilateur **/addmodule**.

    Dans l'exemple suivant, un module de code appelé `Client` a une méthode `Main` de point d'entrée, qui référence une méthode du module `Stringer.dll` créé à l'étape 1.

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    Utilisez la commande suivante pour compiler ce code :

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    Spécifiez l’option **/t:module**, car ce module sera ajouté à un assembly lors d’une étape ultérieure. Spécifiez l’option **/addmodule**, car le code dans `Client`  référence un espace de noms créé par le code dans `Stringer.netmodule`. Le compilateur produit un module appelé `Client.netmodule` qui contient une référence à un autre module, `Stringer.netmodule`.

    >[!NOTE]
    >Les compilateurs C# et Visual Basic prennent en charge la création directe d'assemblys multifichiers à l'aide de deux syntaxes différentes.
    >
    >- Deux compilations créent un assembly à deux fichiers : [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- Une compilation crée un assembly à deux fichiers : [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. Utilisez l’utilitaire [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer le fichier de sortie qui contient le manifeste d’assembly. Ce fichier contient des informations sur les références de tous les modules ou ressources faisant partie de l'assembly.

    À l'invite de commandes, tapez la commande suivante :

    **al** \<*nom_module*> \<*nom_module*> … **/main:** \<*nom_méthode*>  **/out:** \<*nom_fichier*>  **/target:** \<*type_fichier_assembly*>

    Dans cette commande, les arguments *nom_module* spécifient le nom de chaque module à inclure dans l’assembly. L’option **/main:** spécifie le nom de la méthode représentant le point d’entrée de l’assembly. L’option **/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l’assembly. L’option **/target:** indique que l’assembly est un fichier exécutable (.exe) d’application console, un fichier exécutable Windows (.win) ou un fichier bibliothèque (.lib).

    Dans l'exemple suivant, Al.exe crée un assembly qui est un exécutable d'application console appelé `myAssembly.exe`. L’application se compose de deux modules appelés `Client.netmodule` et `Stringer.netmodule`, et du fichier exécutable appelé `myAssembly.exe,` qui contient uniquement les métadonnées de l’assembly. Le point d'entrée de l'assembly est la méthode `Main` de la classe `MainClientApp`, qui est située dans `Client.dll`.

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d’un assembly ou déterminer si un fichier est un assembly ou un module.

## <a name="see-also"></a>Voir aussi

- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)
- [Guide pratique pour afficher le contenu d’un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)
