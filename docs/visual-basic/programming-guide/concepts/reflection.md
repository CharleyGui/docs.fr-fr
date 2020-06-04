---
title: Réflexion
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 43c05a0b3bbfc3dfc304b1aed3f689625a40229a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413178"
---
# <a name="reflection-visual-basic"></a>Réflexion (Visual Basic)
La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent des assemblys, des modules et des types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).  
  
 Voici un exemple simple de réflexion utilisant la méthode statique `GetType`, héritée par tous les types à partir de la classe de base `Object`, pour obtenir le type d’une variable :  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 La sortie est la suivante :  
  
 `System.Int32`  
  
 L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 La sortie est la suivante :  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Vue d’ensemble de la réflexion  
 La réflexion est utile dans les situations suivantes :  
  
- Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme. Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Pour examiner et instancier des types dans un assembly.  
  
- Pour créer de nouveaux types au moment de l’exécution. Utilisez des classes dans <xref:System.Reflection.Emit>.  
  
- Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution. Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sections connexes  
 Pour plus d’informations :  
  
- [Réflexion](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Affichage des informations de type](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Réflexion et types génériques](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation Visual Basic](../index.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
