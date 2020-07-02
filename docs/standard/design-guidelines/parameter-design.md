---
title: Conception de paramètres
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: e0bc52f5679a7771d5690be9f903e677ce611605
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621585"
---
# <a name="parameter-design"></a>Conception de paramètres

Cette section fournit des instructions générales sur la conception des paramètres, y compris des sections avec des indications pour la vérification des arguments. En outre, vous devez vous reporter aux instructions décrites dans [Naming Parameters](naming-parameters.md).

 ✔️ Utilisez le type de paramètre le moins dérivé qui fournit les fonctionnalités requises par le membre.

 Supposons, par exemple, que vous souhaitiez concevoir une méthode qui énumère une collection et imprime chaque élément sur la console. Une telle méthode doit prendre <xref:System.Collections.IEnumerable> comme paramètre, et non <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList> , par exemple.

 ❌N’utilisez pas de paramètres réservés.

 Si une entrée supplémentaire à un membre est nécessaire dans une version ultérieure, une nouvelle surcharge peut être ajoutée.

 ❌N’ont pas de méthodes exposées publiquement qui prennent des pointeurs, des tableaux de pointeurs ou des tableaux multidimensionnels en tant que paramètres.

 Les pointeurs et les tableaux multidimensionnels sont relativement difficiles à utiliser correctement. Dans presque tous les cas, les API peuvent être repensées pour éviter de prendre ces types comme paramètres.

 ✔️ Placez tous les `out` paramètres après la valeur et les `ref` paramètres (à l’exception des tableaux de paramètres), même si cela entraîne une incohérence dans l’ordre des paramètres entre les surcharges (consultez surcharge des [membres](member-overloading.md)).

 Les `out` paramètres peuvent être considérés comme des valeurs de retour supplémentaires et les regrouper ensemble rendent la signature de méthode plus facile à comprendre.

 ✔️ sont cohérentes dans les paramètres d’attribution de noms lors du remplacement des membres ou de l’implémentation des membres d’interface.

 Cela communique mieux la relation entre les méthodes.

### <a name="choosing-between-enum-and-boolean-parameters"></a>Choix entre les paramètres enum et Boolean  
 ✔️ Utilisez des enums si un membre a sinon deux paramètres booléens ou plus.

 ❌N’utilisez pas de valeurs booléennes sauf si vous êtes absolument sûr qu’il n’y aura jamais besoin de plus de deux valeurs.

 Les enums vous donnent de la place pour l’ajout ultérieur de valeurs, mais vous devez être conscient de toutes les implications liées à l’ajout de valeurs aux enums, qui sont décrites dans la section [enum Design](enum.md).

 ✔️ envisagez d’utiliser des valeurs booléennes pour les paramètres de constructeur qui sont véritablement des valeurs à deux États et qui sont simplement utilisées pour initialiser des propriétés booléennes.

### <a name="validating-arguments"></a>Validation des arguments
 ✔️ validez les arguments passés aux membres publics, protégés ou implémentés explicitement. Throw <xref:System.ArgumentException?displayProperty=nameWithType> , ou l’une de ses sous-classes, si la validation échoue.

 Notez que la validation réelle ne doit pas nécessairement se produire dans le membre public ou protégé lui-même. Cela peut se produire à un niveau inférieur dans une routine privée ou interne. Le point principal est que la surface d’exposition entière exposée aux utilisateurs finaux vérifie les arguments.

 ✔️ Levez <xref:System.ArgumentNullException> une exception si un argument null est passé et que le membre ne prend pas en charge les arguments null.

 ✔️ validez les paramètres Enum.

 Ne partez pas du principe que les arguments enum se trouvent dans la plage définie par l’enum. Le CLR permet de convertir n’importe quelle valeur entière en valeur enum, même si la valeur n’est pas définie dans l’enum.

 ❌N’utilisez pas <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> pour les vérifications de plage d’énumération.

 ✔️ N’oubliez pas que les arguments mutables peuvent avoir changé après leur validation.

 Si le membre est sensible à la sécurité, il est recommandé d’effectuer une copie, puis de valider et de traiter l’argument.

### <a name="parameter-passing"></a>Passage de paramètres
 Du point de vue d’un concepteur d’infrastructure, il existe trois groupes principaux de paramètres : les paramètres par valeur, `ref` les paramètres et les `out` paramètres.

 Quand un argument est passé via un paramètre par valeur, le membre reçoit une copie de l’argument réel passé. Si l’argument est un type valeur, une copie de l’argument est placée sur la pile. Si l’argument est un type référence, une copie de la référence est placée sur la pile. La plupart des langages CLR populaires, tels que C#, VB.NET et C++, passent par défaut les paramètres par valeur.

 Quand un argument est passé via un `ref` paramètre, le membre reçoit une référence à l’argument réel passé. Si l’argument est un type valeur, une référence à l’argument est placée sur la pile. Si l’argument est un type référence, une référence à la référence est placée sur la pile. `Ref`les paramètres peuvent être utilisés pour permettre au membre de modifier les arguments passés par l’appelant.

 `Out`les paramètres sont similaires aux `ref` paramètres, avec quelques petites différences. Initialement, le paramètre est considéré comme non assigné et ne peut pas être lu dans le corps du membre avant qu’une valeur ne lui soit assignée. En outre, une valeur doit être assignée au paramètre avant que le membre retourne.

 ❌Évitez d’utiliser des `out` `ref` paramètres ou.

 L' `out` utilisation `ref` de paramètres ou nécessite une expérience avec les pointeurs, la compréhension de la différence entre les types valeur et les types référence, ainsi que la gestion des méthodes avec plusieurs valeurs de retour. En outre, la différence entre les `out` `ref` paramètres et n’est pas largement comprise. Les architectes d’infrastructure qui sont conçus pour un public général ne doivent pas s’attendre à ce que les utilisateurs maîtrisent le travail avec les `out` `ref` paramètres ou.

 ❌NE transmettez pas de types référence par référence.

 Il existe quelques exceptions limitées à la règle, comme une méthode qui peut être utilisée pour échanger des références.

### <a name="members-with-variable-number-of-parameters"></a>Membres avec nombre variable de paramètres
 Les membres qui peuvent prendre un nombre variable d’arguments sont exprimés en fournissant un paramètre de tableau. Par exemple, <xref:System.String> fournit la méthode suivante :

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 Un utilisateur peut ensuite appeler la <xref:System.String.Format%2A?displayProperty=nameWithType> méthode, comme suit :

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 L’ajout du mot clé params C# à un paramètre de tableau modifie le paramètre en paramètre de tableau « params » et fournit un raccourci pour créer un tableau temporaire.

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 Cela permet à l’utilisateur d’appeler la méthode en passant les éléments du tableau directement dans la liste d’arguments.

 `String.Format("File {0} not found in {1}",filename,directory);`

 Notez que le mot clé params ne peut être ajouté qu’au dernier paramètre de la liste de paramètres.

 ✔️ envisagez d’ajouter le mot clé params aux paramètres de tableau si vous vous attendez à ce que les utilisateurs finaux passent des tableaux avec un petit nombre d’éléments. S’il est prévu que beaucoup d’éléments soient passés dans des scénarios courants, les utilisateurs ne passeront probablement pas ces éléments Inline, et le mot clé params n’est donc pas nécessaire.

 ❌Évitez d’utiliser des tableaux de paramètres si l’appelant aurait presque toujours l’entrée déjà dans un tableau.

 Par exemple, les membres avec des paramètres de tableau d’octets ne seraient presque jamais appelés en passant des octets individuels. Pour cette raison, les paramètres de tableau d’octets dans le .NET Framework n’utilisent pas le mot clé params.

 ❌N’utilisez pas de tableaux params si le tableau est modifié par le membre qui prend le paramètre de tableau params.

 Du fait que de nombreux compilateurs transforment les arguments en un tableau temporaire au niveau du site d’appel, le tableau peut être un objet temporaire et, par conséquent, toutes les modifications apportées au tableau seront perdues.

 ✔️ envisagez d’utiliser le mot clé params dans une surcharge simple, même si une surcharge plus complexe ne peut pas l’utiliser.

 Demandez-vous si les utilisateurs ont un tableau de paramètres dans une surcharge, même s’ils n’étaient pas dans toutes les surcharges.

 ✔️ essayez d’ordonner les paramètres afin de pouvoir utiliser le mot clé params.

 ✔️ envisagez de fournir des surcharges et des chemins de code spéciaux pour les appels avec un petit nombre d’arguments dans les API très sensibles aux performances.

 Cela permet d’éviter la création d’objets tableau lorsque l’API est appelée avec un petit nombre d’arguments. Formez les noms des paramètres en utilisant une forme singulière du paramètre de tableau et en ajoutant un suffixe numérique.

 Vous ne devez effectuer cette opération que si vous envisagez de faire de la casse spéciale le chemin de code entier, et non pas simplement de créer un tableau et d’appeler la méthode plus générale.

 ✔️ N’oubliez pas que la valeur NULL peut être passée comme argument de tableau params.

 Vous devez vérifier que le tableau n’a pas la valeur null avant le traitement.

 ❌N’utilisez pas les `varargs` méthodes, également appelées points de suspension.

 Certains langages CLR, tels que C++, prennent en charge une autre convention pour passer des listes de paramètres de variables appelées `varargs` méthodes. La Convention ne doit pas être utilisée dans les frameworks, car elle n’est pas conforme CLS.

### <a name="pointer-parameters"></a>Paramètres du pointeur
 En général, les pointeurs ne doivent pas apparaître dans la surface d’exposition publique d’un Framework de code géré bien conçu. La plupart du temps, les pointeurs doivent être encapsulés. Toutefois, dans certains cas, les pointeurs sont requis pour des raisons d’interopérabilité et l’utilisation de pointeurs dans de tels cas est appropriée.

 ✔️ fournissez une alternative pour tout membre qui accepte un argument de pointeur, car les pointeurs ne sont pas conformes CLS.

 ❌Évitez d’exécuter une vérification coûteuse des arguments de pointeur.

 ✔️ Suivez les conventions courantes liées aux pointeurs lors de la conception de membres avec des pointeurs.

 Par exemple, il n’est pas nécessaire de passer l’index de début, car une opération arithmétique de pointeur simple peut être utilisée pour obtenir le même résultat.

 *Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
