---
title: Constructeurs statiques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881916"
---
# <a name="static-constructors-c-programming-guide"></a>Constructeurs statiques (Guide de programmation C#)
Un constructeur statique est utilisé pour initialiser des données [statiques](../../../csharp/language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois. Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 Les constructeurs statiques ont les propriétés suivantes :  
  
- Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.  
  
- Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique. Notez que le constructeur statique d’un type est appelé quand une méthode statique assignée à un événement ou un délégué est appelée, et non pas quand elle est assignée.
  
- Un constructeur statique ne peut pas être appelé directement.  
  
- L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.  
  
- Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.  
  
- Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.  
  
- Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe `Bus` possède un constructeur statique. Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe. L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
