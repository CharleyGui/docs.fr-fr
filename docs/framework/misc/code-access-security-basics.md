---
title: Notions fondamentales de la sécurité d'accès du code
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 352fa41cb9d3136f853b068d0101a6dcab5dfd7c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645775"
---
# <a name="code-access-security-basics"></a>Notions fondamentales de la sécurité d'accès du code

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Chaque application qui cible le Common Language Runtime (autrement dit, chaque application managée) doit interagir avec le système de sécurité du runtime. Quand une application managée est chargée, son hôte lui attribue automatiquement un jeu d'autorisations. Ces autorisations sont déterminées par les paramètres de sécurité locaux de l'hôte ou par le bac à sable (sandbox) dans lequel se trouve l'application. En fonction de ces autorisations, l'application peut s'exécuter correctement ou générer une exception de sécurité.

L'hôte par défaut pour les applications bureautiques permet d'exécuter du code avec une confiance totale. Ainsi, si votre application cible le bureau, elle dispose d'un jeu d'autorisations illimité. D'autres hôtes ou bacs à sable (sandbox) fournissent un jeu d'autorisations limité pour les applications. Étant donné que le jeu d'autorisations peut changer d'un hôte à l'autre, l'application que vous concevez doit utiliser uniquement les autorisations permises par votre hôte cible.

Vous devez connaître les concepts de sécurité d'accès du code suivants pour écrire des applications efficaces ciblant le Common Language Runtime :

- **Code de type -sécurisé**: Le code de sécurité type est un code qui n’accède aux types que de manière bien définie et admissible. Par exemple, dans le cas d'une référence d'objet valide, le code de type sécurisé peut accéder à la mémoire à des décalages fixes correspondant à des membres de champ réels. Si le code accède à la mémoire à des décalages arbitraires en dehors de la plage de mémoire qui appartient aux champs de cet objet exposés publiquement, il n'est pas de type sécurisé. Pour permettre au code de bénéficier de la sécurité d'accès du code, vous devez utiliser un compilateur qui génère du code de type sécurisé. Pour plus d’informations, consultez la section De la rédaction du Code de sécurité de [type vérifiable](#typesafe_code) plus tard dans ce sujet.

- **Syntaxe impérative et déclarative**: Code qui cible l’heure courante peut interagir avec le système de sécurité en demandant des autorisations, en exigeant que les appelants aient spécifié des autorisations, et en remplaçant certains paramètres de sécurité (étant donné suffisamment de privilèges). Vous utilisez deux formes de syntaxe pour interagir par programmation avec le système de sécurité .NET Framework : la syntaxe déclarative et la syntaxe impérative. Les appels déclaratifs sont effectués à l'aide d'attributs, tandis que les appels impératifs sont réalisés à l'aide de nouvelles instances de classes dans votre code. Certains appels peuvent être effectués de manière impérative uniquement, d'autres peuvent l'être de manière déclarative uniquement et certains peuvent l'être des deux manières.

- **Bibliothèques de classe sécurisées**: Une bibliothèque de classe sécurisée utilise les exigences de sécurité pour s’assurer que les appelants de la bibliothèque ont la permission d’accéder aux ressources que la bibliothèque expose. Par exemple, une bibliothèque de classes sécurisée peut avoir une méthode de création de fichiers qui exige que ses appelants possèdent des autorisations pour créer des fichiers. Le .NET Framework se compose de bibliothèques de classes sécurisées. Vous devez connaître les autorisations nécessaires pour accéder aux bibliothèques utilisées par votre code. Pour plus d’informations, consultez la section [Bibliothèques de classe Using Secure](#secure_library) plus tard dans ce sujet.

- **Code transparent**: En commençant par le cadre .NET 4, en plus d’identifier des autorisations spécifiques, vous devez également déterminer si votre code doit fonctionner comme transparent sur le point de sécurité. Le code transparent de sécurité ne peut pas appeler de types ni de membres critiques de sécurité. Cette règle s'applique aux applications de confiance totale et aux applications partiellement fiables. Pour plus d’informations, voir [Code Sécurité-Transparent](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Écriture de code de type sécurisé vérifié

La compilation juste-à-temps (JIT, Just-In-Time) exécute un processus de vérification qui examine le code et tente de déterminer s'il est de type sécurisé. Le code qui est prouvé au cours de la vérification pour être type-sûr est appelé *code de type-sûr vérifiable*. Le code peut être de type sécurisé, mais non de type sécurisé vérifié, en raison des limites du processus de vérification ou du compilateur. Tous les langages ne sont pas de type sécurisé, et certains compilateurs de langage, tels que Microsoft Visual C++, ne peuvent pas générer de code managé de type sécurisé vérifié. Pour déterminer si le compilateur de langage que vous utilisez génère du code de type sécurisé vérifié, consultez la documentation du compilateur. Si vous utilisez un compilateur de langue qui génère un code de type-sûr vérifiable seulement lorsque vous évitez certaines constructions linguistiques, vous pouvez utiliser [l’outil PEVerify](../tools/peverify-exe-peverify-tool.md) pour déterminer si votre code est vérifiablement de type-sûr.

Le code qui n'est pas de type sécurisé vérifié peut tenter de s'exécuter si la stratégie de sécurité permet au code de contourner la vérification. Cependant, étant donné que la sécurité de type est une partie essentielle du mécanisme du runtime pour isoler les assemblys, la sécurité ne peut pas être appliquée de manière fiable si du code enfreint les règles de la sécurité de type. Par défaut, du code qui n'est pas de type sécurisé n'est autorisé à s'exécuter que s'il provient de l'ordinateur local. Du code mobile doit donc être de type sécurisé.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Utilisation de bibliothèques de classes sécurisées

Si votre code demande et reçoit les autorisations requises par la bibliothèque de classes, il sera autorisé à accéder à la bibliothèque et les ressources exposées par la bibliothèque seront protégées de tout accès non autorisé. Si votre code n'a pas les autorisations appropriées, il ne sera pas autorisé à accéder à la bibliothèque de classes et du code nuisible ne pourra pas utiliser votre code pour accéder aux ressources de manière indirecte. Tout autre code qui appelle votre code doit également être autorisé à accéder à la bibliothèque. Dans le cas contraire, l'exécution de votre code s'en trouvera également entravée.

La sécurité d'accès du code n'élimine pas la possibilité d'une erreur humaine dans l'écriture du code. Cependant, si votre application utilise les bibliothèques de classes sécurisées pour accéder aux ressources protégées, le risque est réduit pour le code de l'application, car les bibliothèques de classes sont soigneusement examinées quant aux éventuels problèmes de sécurité.

## <a name="declarative-security"></a>Sécurité déclarative

La syntaxe de sécurité déclarative utilise [des attributs](../../standard/attributes/index.md) pour placer des informations de sécurité dans les [métadonnées](../../standard/metadata-and-self-describing-components.md) de votre code. Les attributs peuvent être placés au niveau de l'assembly, de la classe ou du membre pour indiquer le type de demande, d'exigence ou de substitution que vous souhaitez utiliser. Les demandes sont utilisées dans les applications qui ciblent le Common Language Runtime pour informer le système de sécurité du runtime des autorisations dont votre application a besoin ou qu'elle refuse. Les exigences et les substitutions sont utilisées dans les bibliothèques pour protéger les ressources des appelants ou substituer le comportement de sécurité par défaut.

> [!NOTE]
> Dans le cadre .NET 4, il y a eu d’importants changements au modèle et à la terminologie de la sécurité du cadre .NET. Pour plus d’informations sur ces changements, voir [changements de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

Pour utiliser des appels de sécurité déclarative, vous devez initialiser les données d'état de l'objet d'autorisation afin qu'elles représentent la forme particulière de l'autorisation dont vous avez besoin. Chaque autorisation intégrée a un attribut auquel une énumération <xref:System.Security.Permissions.SecurityAction> est passée pour décrire le type d'opération de sécurité que vous souhaitez effectuer. Les autorisations acceptent toutefois aussi leurs propres paramètres qui leur sont exclusifs.

Le fragment de code suivant illustre la syntaxe déclarative permettant de demander que les appelants de votre code aient une autorisation personnalisée appelée `MyPermission`. Cette autorisation est une autorisation personnalisée hypothétique et n'existe pas dans le .NET Framework. Dans cet exemple, l'appel déclaratif est placé directement avant la définition de classe, spécifiant que cette autorisation doit être appliquée au niveau de la classe. L’attribut est passé une structure **SecurityAction.Demand** pour spécifier que les appelants doivent avoir cette permission afin de s’exécuter.

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a>Sécurité impérative

La syntaxe de sécurité impérative émet un appel de sécurité en créant une instance de l'objet d'autorisation que vous souhaitez appeler. Vous pouvez utiliser la syntaxe impérative pour effectuer des exigences et des substitutions, mais pas des demandes.

Avant de procéder à l'appel de sécurité, vous devez initialiser les données d'état de l'objet d'autorisation afin qu'elles représentent la forme particulière de l'autorisation dont vous avez besoin. Par exemple, lors <xref:System.Security.Permissions.FileIOPermission> de la création d’un objet, vous pouvez utiliser le constructeur pour initialiser **l’objet FileIOPermission** afin qu’il représente soit un accès illimité à tous les fichiers, soit pas d’accès aux fichiers. Ou, vous pouvez utiliser un autre objet **FileIOPermission,** en passant des paramètres qui indiquent le type d’accès que vous souhaitez que l’objet représente (c’est-à-dire, lire, ajouter ou écrire) et quels fichiers vous voulez que l’objet protège.

Outre utiliser la syntaxe de sécurité impérative pour appeler un objet de sécurité unique, vous pouvez y recourir pour initialiser un groupe d'autorisations dans un jeu d'autorisations. Par exemple, cette technique est la seule façon d’effectuer de manière fiable des appels [d’affirmation](using-the-assert-method.md) sur plusieurs autorisations dans une méthode. Utilisez les classes <xref:System.Security.PermissionSet> et <xref:System.Security.NamedPermissionSet> pour créer un groupe d'autorisations, puis appelez la méthode appropriée pour appeler l'appel de sécurité souhaité.

Vous pouvez utiliser la syntaxe impérative pour effectuer des exigences et des substitutions, mais pas des demandes. Vous pouvez éventuellement utiliser la syntaxe impérative à la place de la syntaxe déclarative pour les exigences et les substitutions quand les informations dont vous avez besoin pour initialiser l'état d'autorisation ne sont connues qu'au moment de l'exécution. Par exemple, si vous souhaitez vous assurer que les appelants ont l'autorisation de lire un certain fichier, mais que vous ne connaissez pas le nom du fichier avant l'exécution, utilisez une exigence impérative. Vous pouvez aussi éventuellement choisir d'utiliser des vérifications impératives au lieu de vérifications déclaratives quand vous avez besoin de déterminer si une condition est valable ou non au moment de l'exécution et, en fonction du résultat du test, de procéder (ou non) à une demande de sécurité.

Le fragment de code suivant illustre la syntaxe impérative permettant de demander que les appelants de votre code aient une autorisation personnalisée appelée `MyPermission`. Cette autorisation est une autorisation personnalisée hypothétique et n'existe pas dans le .NET Framework. Une instance de `MyPermission` est créée dans `MyMethod`, protégeant uniquement cette méthode avec l'appel de sécurité.

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a>Utilisation des classes wrapper managées

La plupart des applications et des composants (excepté les bibliothèques sécurisées) ne doivent pas directement appeler du code non managé, et ce, pour plusieurs raisons. Si du code appelle directement du code non managé, il ne sera pas autorisé à s'exécuter dans de nombreux cas, car du code doit avoir reçu un niveau de confiance élevé pour appeler du code natif. Si la stratégie est modifiée de manière à autoriser l’exécution de cette application, cela peut considérablement affaiblir la sécurité du système, laissant l’application libre d’effectuer quasiment n’importe quelle opération.

De plus, du code qui a l'autorisation d'accéder à du code non managé peut dans l'absolu effectuer pratiquement n'importe quelle opération en appelant dans une interface API non managée. Par exemple, le code qui a la permission <xref:System.Security.Permissions.FileIOPermission> d’appeler du code non menté n’a pas besoin d’accéder à un fichier; il peut simplement appeler un API fichier non géré (Win32) directement, en contournant le fichier géré API qui nécessite **FileIOPermission**. Si du code managé a l'autorisation d'appeler dans du code non managé et n'appelle pas directement dans du code non managé, le système de sécurité ne pourra pas appliquer les restrictions de sécurité de manière fiable puisque le runtime ne peut pas appliquer ces restrictions sur du code non managé.

Si vous souhaitez que votre application effectue une opération qui nécessite l'accès à du code non managé, elle doit le faire par l'intermédiaire d'une classe managée de confiance qui englobe la fonctionnalité requise (si une telle classe existe). Ne créez pas vous-même une classe wrapper s'il en existe déjà une dans une bibliothèque de classes sécurisée. La classe wrapper, qui doit avoir reçu un degré de confiance élevé pour être autorisée à appeler dans du code non managé, est chargée d'exiger que ses appelants aient les autorisations appropriées. Si vous utilisez la classe wrapper, votre code a seulement besoin de demander et de recevoir les autorisations que la classe wrapper exige.

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](using-the-assert-method.md)
- [Sécurité d’accès au code](code-access-security.md)
- [Notions fondamentales de la sécurité d’accès du code](code-access-security-basics.md)
- [Attributs](../../standard/attributes/index.md)
- [Métadonnées et composants auto-décrivants](../../standard/metadata-and-self-describing-components.md)
