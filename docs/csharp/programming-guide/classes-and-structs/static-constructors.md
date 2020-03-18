---
title: Constructeurs statiques - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170115"
---
# <a name="static-constructors-c-programming-guide"></a>Constructeurs statiques (Guide de programmation C#)
Un constructeur statique est utilisé pour initialiser des données [statiques](../../language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois. Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Notes 
Les constructeurs statiques ont les propriétés suivantes :  
  
- Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.  

- Une classe ou struct ne peut pas avoir de constructeur statique.

- Les constructeurs statiques ne peuvent pas être hérités ou surchargés.

- Un constructeur statique ne peut pas être appelé directement et est uniquement destiné à être appelé par le Common Language Runtime (CLR). Il est appelé automatiquement.

- L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.
  
- Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique. Un constructeur statique s’exécute avant le constructeur d’instance. Le constructeur statique d’un type est appelé lorsqu’une méthode statique assignée à un événement ou à un délégué est invoquée et non lorsqu’elle est assignée. Si des initialiseurs de variable de champ statique sont présents dans la classe du constructeur statique, ils seront exécutés dans l’ordre textuel dans lequel ils apparaissent dans la déclaration de classe, immédiatement avant l’exécution du constructeur statique.

- Si vous ne fournissez pas de constructeur statique pour initialiser les champs statiques, tous les champs statiques sont parasésiés à leur valeur par défaut, comme indiqué dans [les valeurs par défaut des types C.](../../language-reference/builtin-types/default-values.md)
  
- Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute. En règle générale, une exception <xref:System.TypeInitializationException> est levée lorsqu’un constructeur statique ne parvient pas à instancier un type ou quand une exception non gérée se produit dans un constructeur statique. Pour les constructeurs statiques implicites qui ne sont pas définis explicitement dans le code source, la résolution des problèmes peut nécessiter l’inspection du code en langage intermédiaire (IL).

- La présence d’un constructeur statique empêche l’ajout de l’attribut de type <xref:System.Reflection.TypeAttributes.BeforeFieldInit>. Cela limite l’optimisation du runtime.

- Un champ déclaré en tant que `static readonly` ne peut être attribué que dans le cadre de sa déclaration ou dans un constructeur statique. Si un constructeur statique explicite n’est pas obligatoire, initialisez les champs statiques lors de la déclaration plutôt que via un constructeur statique pour une meilleure optimisation du runtime.

> [!Note]
> S’il n’est pas directement accessible, la présence d’un constructeur statique explicite doit être documentée pour faciliter la résolution des exceptions de l’initialisation.

### <a name="usage"></a>Usage

- Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.  
- Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.  

- Les constructeurs statiques sont également un endroit pratique pour faire respecter les contrôles en temps d’exécution sur le paramètre de type qui ne peut pas être vérifié au moment de la compilation par des contraintes (contraintes de paramètres de type).

## <a name="example"></a> Exemple
 Dans cet exemple, la classe `Bus` possède un constructeur statique. Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe. L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>spécification du langage C#
Pour plus d’informations, voir la section [Constructeurs statiques](~/_csharplang/spec/classes.md#static-constructors) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Classes statiques et membres de classe statique](./static-classes-and-static-class-members.md)
- [Finaliseurs](./destructors.md)
- [Instructions de conception des constructeurs](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Avertissement de sécurité - CA2121: Les constructeurs statiques doivent être privés](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
