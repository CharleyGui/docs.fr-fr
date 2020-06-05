---
title: Type '<typename>' non défini
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386930"
---
# <a name="type-typename-is-not-defined"></a>Type '\<typename>' non défini
L’instruction a fait référence à un type qui n’a pas été défini. Vous pouvez définir un type dans une instruction de déclaration comme `Enum` , `Structure` , `Class` ou `Interface` .  
  
 **ID d’erreur :** BC30002  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que la définition de type et sa référence utilisent toutes les deux la même orthographe.  
  
- Assurez-vous que la définition de type est accessible à la référence. Par exemple, si le type se trouve dans un autre module et a été déclaré `Private` , déplacez la définition du type vers le module de référence ou déclarez-le `Public` .  
  
- Assurez-vous que l’espace de noms du type n’est pas redéfini dans votre projet. Si c’est le cas, utilisez le `Global` mot clé pour qualifier complètement le nom de type. Par exemple, si un projet définit un espace de noms nommé `System` , le <xref:System.Object?displayProperty=nameWithType> type n’est pas accessible, sauf s’il est qualifié complet avec le `Global` mot clé : `Global.System.Object` .  
  
- Si le type est défini, mais que la bibliothèque d’objets ou la bibliothèque de types dans laquelle il est défini n’est pas inscrite dans Visual Basic, cliquez sur **Ajouter une référence** dans le menu **projet** , puis sélectionnez la bibliothèque d’objets ou la bibliothèque de types appropriée.  
  
- Assurez-vous que le type se trouve dans un assembly qui fait partie du profil de .NET Framework ciblé. Pour plus d’informations, consultez [Dépannage des erreurs de ciblage du .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Voir aussi

- [Espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Enum (instruction)](../statements/enum-statement.md)
- [Structure, instruction](../statements/structure-statement.md)
- [Class (instruction)](../statements/class-statement.md)
- [Interface (instruction)](../statements/interface-statement.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
