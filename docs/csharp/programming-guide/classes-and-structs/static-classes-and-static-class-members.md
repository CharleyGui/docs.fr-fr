---
title: Classes statiques et membres de classe statique - Guide de programmation C#
description: Les classes static ne peuvent pas être instanciées en C#. Vous accédez aux membres d’une classe statique en utilisant le nom de classe lui-même.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: cbfe4b63dc27cf0a0b6aad87c4f011151bacd4e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199014"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Classes statiques et membres de classe statique (Guide de programmation C#)

Une classe [statique](../../language-reference/keywords/static.md) est fondamentalement identique à une classe non statique, à une différence près : une classe statique ne peut pas être instanciée. En d’autres termes, vous ne pouvez pas utiliser l’opérateur [new](../../language-reference/operators/new-operator.md) pour créer une variable du type classe. Étant donné qu’il n’y a aucune variable d’instance, vous accédez aux membres d’une classe statique en utilisant le nom de classe lui-même. Par exemple, si vous avez une classe statique nommée `UtilityClass` qui a une méthode statique publique nommée `MethodA`, vous appelez la méthode comme illustré dans l’exemple suivant :  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Une classe statique peut servir de conteneur pratique pour des ensembles de méthodes qui opèrent simplement sur des paramètres d’entrée et n’ont pas à obtenir ou définir de champs d’instance internes. Par exemple, dans la bibliothèque de classes .NET, la <xref:System.Math?displayProperty=nameWithType> classe statique contient des méthodes qui effectuent des opérations mathématiques, sans qu’il soit nécessaire de stocker ou de récupérer des données qui sont uniques à une instance particulière de la <xref:System.Math> classe. Autrement dit, vous appliquez les membres de la classe en spécifiant le nom de la classe et le nom de la méthode, comme illustré dans l’exemple suivant.  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 Comme c’est le cas avec tous les types de classe, les informations de type pour une classe statique sont chargées par le Runtime .NET lorsque le programme qui référence la classe est chargé. Le programme ne peut pas spécifier exactement quand la classe est chargée. Toutefois, il est garanti qu’elle sera chargée, que ses champs seront initialisés et que son constructeur statique sera appelé avant que la classe soit référencée pour la première fois dans votre programme. Un constructeur statique est appelé une seule fois et une classe statique reste en mémoire pendant la durée de vie du domaine d’application dans lequel votre programme réside.  
  
> [!NOTE]
> Pour créer une classe non statique permettant la création d’une seule instance d’elle-même, consultez [Implémentation d’un singleton en C#](/previous-versions/msp-n-p/ff650316(v=pandp.10)).  
  
 La liste suivante fournit les fonctionnalités principales d’une classe statique :  
  
- Elle contient uniquement des membres statiques.  
  
- Elle ne peut pas être instanciée.  
  
- Elle est verrouillée (sealed).  
  
- Elle ne peut pas contenir de [constructeurs d’instances](./instance-constructors.md).  
  
 La création d’une classe statique est par conséquent très semblable à la création d’une classe contenant uniquement des membres statiques et un constructeur privé. Un constructeur privé empêche la classe d’être instanciée. L’avantage de l’utilisation d’une classe statique est que le compilateur peut vérifier qu’aucun membre d’instance n’a été ajouté par erreur. Le compilateur garantit que les instances de cette classe ne peuvent pas être créées.  
  
 Les classes statiques sont scellées (sealed) et ne peuvent par conséquent pas être héritées. Elles ne peuvent hériter d’aucune classe à part <xref:System.Object>. Les classes static ne peuvent pas contenir un constructeur d’instance. Toutefois, ils peuvent contenir un constructeur statique. Les classes non statiques doivent également définir un constructeur statique si la classe contient des membres statiques qui requièrent une initialisation non triviale. Pour plus d’informations, consultez [Constructeurs statiques](./static-constructors.md).  
  
## <a name="example"></a>Exemple  

 Voici un exemple d’une classe statique qui contient deux méthodes qui convertissent la température des degrés Celsius en degrés Fahrenheit et des degrés Fahrenheit en degrés Celsius :  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Membres static  

 Une classe non statique peut contenir des méthodes, des champs, des propriétés ou des événements statiques. Le membre statique peut être appelé sur une classe même quand aucune instance de la classe n’a été créée. Le membre statique est toujours accessible par le nom de la classe, et non par le nom de l’instance. Une seule copie d’un membre statique existe, quel que soit le nombre d’instances de la classe qui ont été créées. Les méthodes et les propriétés statiques ne peuvent pas accéder à des champs et des événements non statiques dans leur type conteneur, et elles ne peuvent pas accéder à une variable d’instance de n’importe quel objet, sauf si elle est explicitement passée dans un paramètre de méthode.  
  
 Il est plus courant de déclarer une classe non statique avec certains membres statiques que de déclarer une classe entière comme statique. Deux utilisations courantes des champs statiques consistent à conserver un décompte du nombre d’objets qui ont été instanciés ou à stocker une valeur qui doit être partagée entre toutes les instances.  
  
 Les méthodes statiques peuvent être surchargées mais pas substituées, car elles appartiennent à la classe et non pas à une instance de la classe.  
  
 Bien qu’un champ ne puisse pas être déclaré en tant que `static const`, un champ [const](../../language-reference/keywords/const.md) est essentiellement statique dans son comportement. Il appartient au type, pas aux instances du type. Par conséquent, `const` les champs sont accessibles à l’aide de la même `ClassName.MemberName` notation que celle utilisée pour les champs statiques. Aucune instance d’objet n’est requise.  
  
 C# ne prend pas en charge les variables locales statiques (autrement dit, les variables déclarées dans la portée de la méthode).  
  
 Vous déclarez des membres de classe statique en utilisant le mot clé `static` avant le type de retour du membre, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Les membres statiques sont initialisés avant le premier accès au membre statique et avant que le constructeur statique, s’il en existe un, soit appelé. Pour accéder à un membre de classe statique, utilisez le nom de la classe au lieu d’un nom de variable pour spécifier l’emplacement du membre, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Si votre classe contient des champs statiques, fournissez un constructeur statique qui les initialise quand la classe est chargée.  
  
 Un appel à une méthode statique génère une instruction d’appel en langage MSIL (Microsoft Intermediate Language), tandis qu’un appel à une méthode d’instance génère une `callvirt` instruction, qui vérifie également les références d’objet null. Toutefois, la plupart du temps, l’écart de performances entre les deux n’est pas significatif.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, voir [Classes statiques](~/_csharplang/spec/classes.md#static-classes) et [Membres statiques et d’instances](~/_csharplang/spec/classes.md#static-and-instance-members) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [static](../../language-reference/keywords/static.md)
- [Classes](./classes.md)
- [class](../../language-reference/keywords/class.md)
- [Constructeurs statiques](./static-constructors.md)
- [Constructeurs d’instances](./instance-constructors.md)
