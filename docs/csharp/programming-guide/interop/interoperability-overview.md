---
title: Vue d'ensemble de l'interopérabilité - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 2c9eb2a8e6c2db8dc06ebe48ca6eb37d5cf638e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700729"
---
# <a name="interoperability-overview-c-programming-guide"></a>Vue d'ensemble de l'interopérabilité (Guide de programmation C#)
Cette rubrique décrit les méthodes qui permettent une interopérabilité entre le code managé C# et le code non managé.  
  
## <a name="platform-invoke"></a>Appel de plateforme  
 L’*appel de code non managé* est un service qui permet au code managé d’appeler des fonctions non managées implémentées dans des bibliothèques de liens dynamiques (DLL), telles que celles de l’API Windows Microsoft. Il localise et appelle une fonction exportée, puis marshale ses arguments (entiers, chaînes, tableaux, structures, etc) au-delà des limites d’interopérabilité, selon les besoins.  
  
Pour plus d’informations, voir [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md) and [How to use platform invoke to play a WAV file](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> Le [common language runtime](../../../standard/clr.md) (CLR) gère l’accès aux ressources système. Le fait d’appeler du code non managé extérieur au CLR contourne ce mécanisme, ce qui présente un risque de sécurité. Par exemple, du code non managé peut appeler directement des ressources dans du code non managé en contournant les mécanismes de sécurité CLR. Pour plus d’informations, consultez [Sécurité dans .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>Interopérabilité C++  
 Vous pouvez utiliser l’interopérabilité C++, également appelée It Just Works (IJW), pour encapsuler une classe C++ native de sorte qu’elle puisse être utilisée par du code créé en C# ou un autre langage du .NET Framework. Pour ce faire, écrivez du code C++ pour encapsuler un composant DLL ou COM natif. Contrairement à d’autres langages du .NET Framework, Visual C++ comprend le support de l’interopérabilité qui permet à du code managé et non managé de se trouver dans la même application et même dans le même fichier. Vous pouvez ensuite générer le code C++ à l’aide du commutateur de compilateur **/clr** pour créer un assembly managé. Enfin, ajoutez une référence à l’assembly dans votre projet C# et utilisez les objets encapsulés comme vous le feriez pour les autres classes managées.  
  
## <a name="exposing-com-components-to-c"></a>Exposer des composants COM au langage C\#
 Vous pouvez utiliser un composant COM d’un projet C#. Les étapes générales sont les suivantes :  
  
1. Recherchez le composant COM à utiliser et enregistrez-le. Utilisez regsvr32.exe pour inscrire ou désinscrire une DLL COM.  
  
2. Ajoutez au projet une référence au composant COM ou à la bibliothèque de types.  
  
     Quand vous ajoutez la référence, Visual Studio utilise le fichier [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md), qui prend comme entrée une bibliothèque de types, pour générer un assembly d’interopérabilité .NET Framework. L’assembly, également appelé wrapper RCW, contient des classes et des interfaces managées qui encapsulent les classes et les interfaces COM qui se trouvent dans la bibliothèque de types. Visual Studio ajoute au projet une référence à l’assembly généré.  
  
3. Créez une instance d’une classe qui est définie dans le wrapper RCW. Une instance de l’objet COM est ainsi créée.  
  
4. Utilisez l’objet comme vous utiliseriez tout autre objet managé. Lorsque l’objet est récupéré par le garbage collection, l’instance de l’objet COM est également libérée de la mémoire.  
  
 Pour plus d’informations, consultez [Exposition de composants COM au .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Exposition du langage C# à COM  
 Les clients COM peuvent utiliser des types C# qui ont été correctement exposés. Les étapes de base pour exposer des types C# sont les suivantes :  
  
1. Ajoutez des attributs d’interopérabilité dans le projet C#.  
  
     Vous pouvez rendre visible un assembly COM en modifiant les propriétés de projet Visual C#. Pour plus d’informations, consultez [Informations de l’assembly, boîte de dialogue](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Générez une bibliothèque de types COM et inscrivez-la pour l’utilisation de COM.  
  
     Vous pouvez modifier les propriétés de projet Visual C# pour inscrire automatiquement l’assembly C# pour COM Interop. Visual Studio utilise le fichier [Regasm.exe (outil d’inscription de l’assembly)](../../../framework/tools/regasm-exe-assembly-registration-tool.md) avec le commutateur de ligne de commande `/tlb`, qui prend comme entrée un assembly managé pour générer une bibliothèque de types. Cette bibliothèque de types décrit les types `public` de l’assembly et ajoute les entrées du Registre pour que les clients COM puissent créer des classes managées.  
  
 Pour plus d’informations, consultez [Exposition de composants .NET Framework à COM](../../../framework/interop/exposing-dotnet-components-to-com.md) et [Exemple de classe COM](./example-com-class.md).  
  
## <a name="see-also"></a>Voir aussi

- [Améliorer les performances d’interopérabilité](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Introduction à l’interopérabilité entre COM et .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Introduction à COM Interop en Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Marshaling entre du code managé et non managé](../../../framework/interop/interop-marshaling.md)
- [Interopération avec code non traité](../../../framework/interop/index.md)
- [Guide de programmation C#](../index.md)
