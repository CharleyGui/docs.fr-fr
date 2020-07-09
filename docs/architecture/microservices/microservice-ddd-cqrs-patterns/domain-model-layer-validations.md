---
title: Conception de validations dans la couche de modèle de domaine
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les concepts clés des validations de modèle de domaine.
ms.date: 10/08/2018
ms.openlocfilehash: 94df2d6441581fbbae479da2524d6ffce2037d68
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100910"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Concevoir des validations dans la couche du modèle de domaine

Dans la conception DDD, les règles de validation peuvent être considérées comme des invariants. La responsabilité principale d’un agrégat est d’appliquer des invariants aux changements d’état pour toutes les entités de cet agrégat.

Les entités de domaine doivent toujours être des entités valides. Pour un objet, il existe un certain nombre d’invariants qui doivent toujours avoir la valeur true. Par exemple, un objet d’élément de commande doit toujours avoir une quantité qui doit être un entier positif, ainsi qu’un nom d’article et un prix. Par conséquent, il incombe aux entités de domaine (en particulier celles de la racine d’agrégat) de mettre en application les invariants, et un objet d’entité ne doit pas pouvoir exister s’il n’est pas valide. Les règles invariantes sont simplement exprimées sous la forme de contrats. Quand elles sont enfreintes, des exceptions ou des notifications sont déclenchées.

Le raisonnement derrière cette règle est que de nombreux bogues se produisent car les objets sont dans un état dans lequel ils n’auraient jamais dû se trouver. Ce qui suit en est une bonne explication de Greg Young dans une [discussion en ligne](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/) :

Supposons que nous disposons désormais d’un service SendUserCreationEmailService qui prend un UserProfile... Comment pouvons-nous justifier, dans ce service, que le nom ne soit pas null ? Le vérifions-nous à nouveau ? Ou plus probablement... vous ne vous souciez simplement pas de la vérification et « espérez que tout se passera au mieux » : vous espérez que quelqu’un a pris la peine de le valider avant de vous l’envoyer. Bien entendu, en utilisant TDD, l’un des premiers tests que nous devons écrire est que si j’envoie un client avec un nom null, une erreur doit être déclenchée. Mais une fois que nous commençons à écrire ce genre de tests encore et encore, nous réalisons ceci : « Si nous n’avions pas autorisé qu’un nom devienne null, nous n’aurions pas tous ces tests ».

## <a name="implement-validations-in-the-domain-model-layer"></a>Implémenter des validations dans la couche du modèle de domaine

Les validations sont généralement implémentées dans des constructeurs d’entité de domaine ou dans des méthodes qui peuvent mettre à jour l’entité. Il existe plusieurs façons d’implémenter des validations, comme la vérification des données et la levée d’exceptions si la validation échoue. Il existe également des modèles plus avancés comme l’utilisation du modèle Spécification pour les validations, et le modèle Notification pour retourner une collection d’erreurs au lieu de retourner une exception pour chaque validation quand elle se produit.

### <a name="validate-conditions-and-throw-exceptions"></a>Valider des conditions et lever des exceptions

L’exemple de code suivant illustre l’approche de validation la plus simple dans une entité de domaine en levant une exception. La table de références figurant à la fin de cette section indique des liens vers des implémentations plus avancées basées sur les modèles abordés précédemment.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

La nécessité de garantir que l’état interne n’a pas changé ou que toutes les mutations pour une méthode se sont produites constituerait un meilleur exemple. Ainsi, l’implémentation suivante laisse l’objet dans un état non valide :

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Si la valeur de l’état n’est pas valide, la première ligne d’adresse et la ville ont déjà été modifiées. Cela peut rendre l’adresse non valide.

Une approche similaire peut être utilisée dans le constructeur de l’entité, en déclenchant une exception pour s’assurer que l’entité est valide une fois qu’elle a été créée.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Utiliser des attributs de validation dans le modèle basé sur des annotations de données

Les annotations de données, comme les attributs Required ou MaxLength, peuvent être utilisées pour configurer des propriétés de champ de base de données EF Core, comme expliqué en détail dans la section [Mappage de table](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping), mais [elles ne fonctionnent plus pour la validation des entités dans EF Core](https://github.com/dotnet/efcore/issues/3680) (tout comme la méthode <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType>), comme c’était le cas depuis EF 4.x dans .NET Framework.

Les annotations de données et l' <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface peuvent toujours être utilisées pour la validation du modèle lors de la liaison de modèle, avant l’invocation des actions du contrôleur, comme d’habitude, mais ce modèle est destiné à être un ViewModel ou un DTO, et il s’agit d’un problème de modèle de domaine ou d’API.

La différence conceptuelle étant claire, vous pouvez toujours utiliser des annotations de données et `IValidatableObject` dans la classe d’entité pour la validation si vos actions reçoivent un paramètre d’objet de classe d’entité, ce qui n’est pas recommandé. Dans ce cas, la validation se produit lors de la liaison de modèle, juste avant l’appel de l’action, et vous pouvez vérifier la propriété ModelState. IsValid du contrôleur pour vérifier le résultat, mais là encore, il se produit dans le contrôleur, et non pas avant de rendre persistant l’objet d’entité dans le DbContext, comme c’était le cas depuis EF 4. x.

Vous pouvez toujours implémenter une validation personnalisée dans la classe d’entité à l’aide d’annotations de données et de la `IValidatableObject.Validate` méthode, en substituant la méthode SaveChanges de DbContext.

Vous pouvez voir un exemple d’implémentation pour la validation d’entités `IValidatableObject` dans [ce commentaire sur GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539). Cet exemple n’effectue pas de validations basées sur les attributs, mais il doit être facile à implémenter à l’aide de la réflexion dans le même remplacement.

Toutefois, du point de vue DDD, le modèle de domaine est mieux conservé avec l’utilisation d’exceptions dans les méthodes de comportement de votre entité, ou en implémentant les modèles de spécification et de notification pour appliquer des règles de validation.

Il peut être judicieux d’utiliser des annotations de données au niveau de la couche Application dans les classes ViewModel (plutôt que des entités de domaine) qui accepteront des entrées, pour permettre la validation de modèle dans la couche d’interface utilisateur. Toutefois, cela ne doit pas être effectué à l’exclusion de la validation dans le modèle de domaine.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Validation d’entités en implémentant le modèle de spécification et le modèle de notification

Enfin, une approche plus élaborée pour implémenter des validations dans le modèle de domaine consiste à implémenter le modèle Spécification conjointement avec le modèle Notification, comme expliqué dans certaines des ressources supplémentaires répertoriées ultérieurement.

Il convient de mentionner que vous pouvez également utiliser un seul de ces modèles, par exemple en effectuant la validation manuellement avec des instructions de contrôle, mais en utilisant le modèle Notification pour empiler des erreurs de validation et en retourner la liste.

### <a name="use-deferred-validation-in-the-domain"></a>Utiliser la validation différée dans le domaine

Il existe différentes approches pour traiter les validations différées dans le domaine. Dans son livre [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon les décrit dans la section relative à la validation.

### <a name="two-step-validation"></a>Validation en deux étapes

Considérons également la validation en deux étapes. Utilisez la validation au niveau des champs sur vos objets de transfert de données (DTO) de commande et la validation au niveau du domaine à l’intérieur de vos entités. Pour cela, retournez un objet de résultat plutôt que des exceptions afin de faciliter la gestion des erreurs de validation.

En utilisant la validation de champ avec des annotations de données, par exemple, vous ne dupliquez pas la définition de la validation. L’exécution peut toutefois être à la fois côté serveur et côté client dans le cas d’objets DTO (commandes et ViewModels, par exemple).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Rachel appel. Présentation de la validation de modèle dans ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Ajout de la validation** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Remplacement des exceptions levées par notification dans les validations** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Modèles de spécification et de notification** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Validation dans la conception pilotée par domaine (DDD)** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Le Jack Colin. Validation du modèle de domaine** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy bogard. Validation dans un monde DDD** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Précédent](enumeration-classes-over-enum-types.md) 
>  [Suivant](client-side-validation.md)
