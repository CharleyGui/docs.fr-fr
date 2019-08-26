---
title: Transfert de type dans le Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921414"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Transfert de type dans le Common Language Runtime
Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.  
  
 Par exemple, supposons qu’une application utilise la classe `Example` dans un assembly appelé `Utility.dll`. Les développeurs de `Utility.dll` peuvent décider de refactoriser l’assembly, et dans le cadre du processus sont susceptibles de déplacer la classe `Example` vers un autre assembly. Si l’ancienne version de `Utility.dll` est remplacée par la nouvelle version de `Utility.dll` et son assembly auxiliaire, l’application utilisant la classe `Example` est mise en échec car elle ne peut pas localiser la classe `Example` dans la nouvelle version de `Utility.dll`.  
  
 Les développeurs de `Utility.dll` peuvent éviter ce problème en transférant les demandes pour la classe `Example` à l’aide de l’attribut <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>. Si l’attribut a été appliqué à la nouvelle version de `Utility.dll`, les demandes associées à la classe `Example` sont transmises à l’assembly qui contient la classe. L’application existante continue à fonctionner normalement, sans nouvelle compilation.  
  
> [!NOTE]
> Dans .NET Framework version 2.0, il est impossible de transférer des types provenant d’assemblys écrits en Visual Basic. Toutefois, une application écrite en Visual Basic peut utiliser des types transférés. Autrement dit, si l’application utilise un assembly codé en C# ou C++ et qu’un type de cet assembly est transmis à un autre assembly, l’application Visual Basic peut utiliser le type transféré.  
  
## <a name="forwarding-types"></a>Transfert de types  
 Le transfert de type se décompose en quatre étapes :  
  
1. Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.  
  
2. Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé. Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. Compilez l’assembly qui contient désormais le type.  
  
4. Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type. Par exemple, si vous compilez un fichier C# de la ligne de commande, utilisez l’option [/reference (Options du compilateur C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assembly contenant le type. Dans C++, utilisez la directive [#using](/cpp/preprocessor/hash-using-directive-cpp) dans le fichier source pour spécifier l’assembly contenant le type.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Transfert de type (C++-CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [Directive #using](/cpp/preprocessor/hash-using-directive-cpp)
