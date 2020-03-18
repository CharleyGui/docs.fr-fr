---
title: Transfert de type dans le Common Language Runtime
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160363"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Transfert de type dans le Common Language Runtime
Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.  
  
 Supposons, par exemple, `Example` qu’une application utilise la classe dans un assemblage nommé *Utility.dll*. Les développeurs de *Utility.dll* pourraient décider de refactor l’assemblage, et dans le processus, ils pourraient déplacer la `Example` classe à un autre assemblage. Si l’ancienne version de *Utility.dll* est remplacée par la nouvelle version de *Utility.dll* et son assemblage compagnon, l’application qui utilise la `Example` classe échoue parce qu’elle ne peut pas localiser la `Example` classe dans la nouvelle version de *Utility.dll*.  
  
 Les développeurs de *Utility.dll* peuvent éviter cela `Example` en transmettant des demandes pour la classe, en utilisant l’attribut. <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> Si l’attribut a été appliqué à la nouvelle version `Example` de *Utility.dll*, les demandes pour la classe sont transmises à l’assemblage qui contient maintenant la classe. L’application existante continue à fonctionner normalement, sans nouvelle compilation.  
  
> [!NOTE]
> Dans .NET Framework version 2.0, il est impossible de transférer des types provenant d’assemblys écrits en Visual Basic. Toutefois, une application écrite en Visual Basic peut utiliser des types transférés. Autrement dit, si l’application utilise un assembly codé en C# ou C++ et qu’un type de cet assembly est transmis à un autre assembly, l’application Visual Basic peut utiliser le type transféré.  
  
## <a name="forward-types"></a>Types avant  
 Le transfert de type se décompose en quatre étapes :  
  
1. Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.  

2. Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé. Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Compilez l’assembly qui contient désormais le type.  

4. Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type. Par exemple, si vous compilez un fichier C à partir de la ligne de commande, utilisez [l’option de référence (options de compilation C)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assemblage qui contient le type. Dans C++, utilisez la directive [#using](/cpp/preprocessor/hash-using-directive-cpp) dans le fichier source pour spécifier l’assembly contenant le type.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Type d’end avant (C/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [directive #using](/cpp/preprocessor/hash-using-directive-cpp)
