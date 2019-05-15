---
title: 'Procédure : déterminer le nom qualifié complet d’un assembly'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f1dbfde5e13d771f82ab1542e02de4c72b68678
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607747"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a>Procédure : déterminer le nom qualifié complet d’un assembly
Pour découvrir le nom qualifié complet d’un assembly dans le Global Assembly Cache, utilisez l’outil Global Assembly Cache ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Voir [Guide pratique pour visualiser le contenu du Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Pour les assemblys qui ne sont pas dans le Global Assembly Cache, vous pouvez obtenir le nom qualifié complet de l’assembly de différentes façons : vous pouvez utiliser du code pour afficher les informations sur la console ou dans une variable, ou bien vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contiennent le nom qualifié complet.  
  
- Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet. Vous pouvez utiliser cette approche que l'assembly se trouve ou non dans le GAC. Cet exemple en fournit une illustration.  
  
- Si vous connaissez le chemin d'accès de l'assembly dans le système de fichiers, vous pouvez appeler la méthode statique (`Shared` en Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> pour obtenir le nom complet de l'assembly. Voici un exemple simple.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
- Vous pouvez utiliser le [Désassembleur IL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contiennent le nom complet.  
  
 Pour plus d’informations sur la définition des attributs d’un assembly, comme la version, la culture et le nom d’assembly, consultez [Définition des attributs d’assembly](../../../docs/framework/app-domains/set-assembly-attributes.md). Pour plus d’informations sur l’attribution d’un nom fort à un assembly, consultez [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment afficher sur la console le nom complet d'un assembly contenant une classe spécifiée. Comme il récupère le nom d'un assembly que l'application a déjà chargé, peu importe si l'assembly se trouve dans le GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Noms d’assemblys](../../../docs/framework/app-domains/assembly-names.md)
- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)
- [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
