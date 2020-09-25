---
title: Comment implémenter et appeler une méthode d’extension personnalisée (Guide de programmation C#)
description: Découvrez comment implémenter des méthodes d’extension pour n’importe quel type .NET. Le code client peut utiliser vos méthodes en ajoutant une référence à une DLL et en ajoutant une directive using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: de4cc423e1823351305a23f331b082aa66add1a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190434"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Comment implémenter et appeler une méthode d’extension personnalisée (Guide de programmation C#)

Cette rubrique montre comment implémenter vos propres méthodes d’extension pour n’importe quel type .NET. Le code client peut utiliser vos méthodes d’extension en ajoutant une référence à la DLL qui les contient, et en ajoutant une directive [using](../../language-reference/keywords/using-directive.md) qui spécifie l’espace de noms dans lequel les méthodes d’extension sont définies.  
  
## <a name="to-define-and-call-the-extension-method"></a>Pour définir et appeler la méthode d’extension  
  
1. Définissez une classe statiquepour contenir la méthode d’extension.  
  
     La classe doit être visible par le code client. Pour plus d’informations sur les règles d’accessibilité, consultez [Modificateurs d’accès](./access-modifiers.md).  
  
2. Implémentez la méthode d’extension en tant que méthode statique avec au moins la même visibilité que la classe conteneur.  
  
3. Le premier paramètre de la méthode spécifie le type sur lequel la méthode opère. Il doit être précédé du modificateur [this](../../language-reference/keywords/this.md).  
  
4. Dans le code appelant, ajoutez une directive `using` pour spécifier l’[espace de noms](../../language-reference/keywords/namespace.md) qui contient la classe de méthode d’extension.  
  
5. Appelez les méthodes comme s’il s’agissait de méthodes d’instance sur le type.  
  
     Notez que le premier paramètre n’est pas spécifié par le code appelant, car il représente le type sur lequel l’opérateur est appliqué, et le compilateur connaît déjà le type de votre objet. Vous devez fournir des arguments uniquement pour les paramètres 2 à `n`.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant implémente une méthode d’extension nommée `WordCount` dans la classe `CustomExtensions.StringExtension`. La méthode opère sur la classe <xref:System.String>, qui est spécifiée comme premier paramètre de méthode. L’espace de noms `CustomExtensions` est importé dans l’espace de noms d’application, et la méthode est appelée à l’intérieur de la méthode `Main`.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a>Sécurité .NET  

 Les méthodes d’extension ne présentent aucune faille de sécurité spécifique. Elles ne peuvent jamais être utilisées pour emprunter l’identité des méthodes existantes sur un type, car toutes les collisions de noms sont résolues en faveur de l’instance ou de la méthode statique définie par le type lui-même. Les méthodes d’extension ne peuvent pas accéder à des données privées dans la classe étendue.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Méthodes d’extension](./extension-methods.md)
- [LINQ (Language Integrated Query)](../../linq/linq-in-csharp.md)
- [Classes statiques et membres de classe statique](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [namespace](../../language-reference/keywords/namespace.md)
