---
title: Types de changements cassants
description: Découvrez comment .NET Core tente de maintenir la compatibilité pour les développeurs sur les versions de .NET et quel type de modification est considéré comme une modification avec rupture.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628590"
---
# <a name="changes-that-affect-compatibility"></a>Modifications qui affectent la compatibilité

Tout au long de son histoire, .NET a tenté de maintenir un niveau élevé de compatibilité de version en version et entre les différentes déclinaisons de .NET. Cette philosophie s’applique toujours avec .NET Core. Bien que .NET Core peut être considéré comme une nouvelle technologie indépendante du .NET Framework, deux facteurs majeurs limitent la capacité de .NET Core à diverger du .NET Framework :

- Un grand nombre de développeurs ont développé à la base ou continuent à développer des applications .NET Framework. Ils s’attendent à un comportement cohérent entre les implémentations de .NET.

- Les projets de bibliothèque .NET Standard permettent aux développeurs de créer des bibliothèques qui ciblent les API communes partagées par .NET Core et .NET Framework. Les développeurs s’attendent à ce qu’une bibliothèque utilisée dans une application .NET Core se comporte comme la bibliothèque utilisée dans une application .NET Framework.

En plus de la compatibilité entre les implémentations de .NET, les développeurs s’attendent à un haut niveau de compatibilité entre les versions de .NET Core. En particulier, le code écrit pour une version antérieure de .NET Core doit s’exécuter sans problème sur une version ultérieure de .NET Core. En fait, de nombreux développeurs s’attendent à ce que les nouvelles API dans les dernières versions de .NET Core soient également compatibles avec les versions préliminaires dans lesquelles ces API ont été introduites.

Cet article décrit les catégories de modifications de compatibilité (ou changements cassants) et la manière dont l’équipe .NET évalue les modifications dans chacune de ces catégories. Comprendre comment l’équipe .NET approche des modifications avec rupture possibles est particulièrement utile pour les développeurs qui ouvrent des requêtes de tirage dans le référentiel GitHub [dotnet/Runtime](https://github.com/dotnet/runtime) qui modifient le comportement des API existantes.

> [!NOTE]
> Pour une définition des catégories de compatibilité, comme la compatibilité binaire et la compatibilité descendante, consultez [Catégories de changements cassants](categories.md).

Les sections suivantes décrivent les catégories de modifications apportées aux API .NET Core et leur impact sur la compatibilité des applications. Les modifications sont autorisées ✔️, les ❌rejetées ou nécessitent un jugement et une évaluation de la ❓ du comportement prévisible, évident et cohérent.

> [!NOTE]
> En plus de servir de guide pour l’évaluation des modifications apportées aux bibliothèques .NET Core, les développeurs de bibliothèques peuvent également utiliser ces critères pour évaluer les modifications apportées à leurs bibliothèques qui ciblent plusieurs implémentations et versions de .NET.

## <a name="modifications-to-the-public-contract"></a>Modifications au contrat public

Les modifications de cette catégorie modifient la surface d’exposition publique d’un type. La plupart des modifications de cette catégorie ne sont pas autorisées dans la mesure où elles enfreignent une *compatibilité descendante* (la possibilité pour une application qui a été développée avec une version précédente d’une API de s’exécuter sans recompilation sur une version ultérieure).

### <a name="types"></a>Types

- ✔️ **autorisé : suppression d’une implémentation d’interface d’un type quand l’interface est déjà implémentée par un type de base**

- ❓ **Nécessite un jugement : ajout d’une nouvelle implémentation d’interface à un type**

  Il s’agit d’une modification acceptable, car elle n’affectera pas les clients existants. Toutes les modifications au type doivent fonctionner dans les limites des modifications acceptables définies ici pour la nouvelle implémentation afin de rester acceptables. Une prudence extrême est nécessaire lors de l’ajout d’interfaces qui affectent directement la capacité d’un concepteur ou sérialiseur à générer du code ou des données qui ne peuvent pas être consommées à un bas niveau. Par exemple, l’interface <xref:System.Runtime.Serialization.ISerializable>.

- ❓ **Nécessite un jugement : présentation d’une nouvelle classe de base**

  Un type peut être introduit dans une hiérarchie entre deux types existants s’il n’introduit pas de nouveaux membres [abstraits](../../csharp/language-reference/keywords/abstract.md) ou si vous modifiez la sémantique ou le comportement de types existants. Par exemple, dans .NET Framework 2.0, la classe <xref:System.Data.Common.DbConnection> est devenue une classe de base pour <xref:System.Data.SqlClient.SqlConnection>, qui était précédemment dérivée directement de <xref:System.ComponentModel.Component>.

- ✔️ **autorisé : déplacement d’un type d’un assembly vers un autre**

  L' *ancien* assembly doit être marqué avec le <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> qui pointe vers le nouvel assembly.

- ✔️ **autorisées : la modification d’un type [struct](../../csharp/language-reference/builtin-types/struct.md) en type `readonly struct`**

  La modification d’un type de `readonly struct` en type de `struct` n’est pas autorisée.

- ✔️ **autorisé : ajout du mot clé [sealed](../../csharp/language-reference/keywords/sealed.md) ou [abstract](../../csharp/language-reference/keywords/abstract.md) à un type lorsqu’il n’y a aucun constructeur *accessible* (public ou protégé)**

- ✔️ **autorisé : extension de la visibilité d’un type**

- ❌ **interdite : modification de l’espace de noms ou du nom d’un type**

- ❌ **interdit : renommer ou supprimer un type public**

   Cela empêche tout code qui utilise le type renommé ou supprimé de fonctionner.

- ❌ **interdite : modification du type sous-jacent d’une énumération**

   Il s’agit d’un changement cassant au niveau de la compilation et du comportement ainsi qu’un changement cassant binaire qui peut rendre les arguments d’attribut non analysables.

- ❌ **interdit : scelle un type qui a été précédemment non scellé**

- ❌ **interdite : ajout d’une interface à l’ensemble des types de base d’une interface**

   Si une interface implémente une interface qu’elle n’implémentait pas précédemment, tous les types implémentant la version d’origine de l’interface cessent de fonctionner.

- ❓ **Nécessite un jugement : la suppression d’une classe de l’ensemble de classes de base ou d’une interface de l’ensemble des interfaces implémentées**

  Il existe une exception à la règle pour la suppression de l’interface : vous pouvez ajouter l’implémentation d’une interface qui dérive de l’interface supprimée. Par exemple, vous pouvez supprimer <xref:System.IDisposable> si le type ou l’interface implémente désormais <xref:System.ComponentModel.IComponent>, qui implémente <xref:System.IDisposable>.

- ❌ **interdite : remplacement d’un type de `readonly struct` par un type [struct](../../csharp/language-reference/builtin-types/struct.md)**

  Toutefois, la modification d’un type de `struct` en type `readonly struct` est autorisée.

- ❌ **interdite : la modification d’un type [struct](../../csharp/language-reference/builtin-types/struct.md) en type `ref struct`, et vice versa**

- ❌ **interdite : réduction de la visibilité d’un type**

   Toutefois, l’augmentation de la visibilité d’un type est autorisée.

### <a name="members"></a>Membres

- ✔️ **autorisé : extension de la visibilité d’un membre qui n’est pas [virtuel](../../csharp/language-reference/keywords/sealed.md)**

- ✔️ **autorisé : ajout d’un membre abstrait à un type public qui n’a pas de constructeurs (publics ou protégés) *accessibles* , ou le type est [sealed](../../csharp/language-reference/keywords/sealed.md)**

  Toutefois, l’ajout à un membre abstrait à un type qui a des constructeurs accessibles (publics ou protégés) et n’est pas `sealed` n’est pas autorisé.

- ✔️ **autorisé : restriction de la visibilité d’un membre [protégé](../../csharp/language-reference/keywords/protected.md) quand le type n’a pas de constructeurs accessibles (publics ou protégés) ou si le type est [sealed](../../csharp/language-reference/keywords/sealed.md)**

- ✔️ **autorisé : déplacement d’un membre dans une classe située plus haut dans la hiérarchie que le type à partir duquel il a été supprimé**

- ✔️ **autorisé : ajout ou suppression d’un remplacement**

  L’introduction d’une substitution peut amener les consommateurs précédents à ignorer le remplacement lors de l’appel de la [base](../../csharp/language-reference/keywords/base.md).

- ✔️ **autorisé : ajout d’un constructeur à une classe, avec un constructeur sans paramètre si la classe n’avait pas précédemment de constructeurs**

   Cependant, ajouter un constructeur à une classe qui n’avait auparavant aucun constructeur *sans* ajouter le constructeur sans paramètre n’est pas autorisé.

- ✔️ **autorisées : [la](../../csharp/language-reference/keywords/virtual.md) modification d’un membre de [abstract](../../csharp/language-reference/keywords/abstract.md) en Virtual**

- ✔️ **autorisées : la modification d’un `ref readonly` en `ref` valeur de retour (à l’exception des méthodes virtuelles ou des interfaces)**

- ✔️ **autorisé : suppression de [ReadOnly](../../csharp/language-reference/keywords/readonly.md) d’un champ, sauf si le type statique du champ est un type valeur mutable**

- ✔️ **autorisé : appel d’un nouvel événement qui n’a pas été défini précédemment**

- ❓ **Nécessite un jugement : ajout d’un nouveau champ d’instance à un type**

   Cette modification a un impact sur la sérialisation.

- ❌ **interdit : renommer ou supprimer un membre ou un paramètre public**

   Cela empêche tout code qui utilise le membre ou paramètre renommé ou supprimé de fonctionner.

   Cela comprend la suppression ou le changement de nom d’une méthode Getter ou Setter d’une propriété, ainsi que l’attribution d’un nouveau nom ou la suppression des membres de l’énumération.

- ❌ **interdite : ajout d’un membre à une interface**

- ❌ **interdite : modification de la valeur d’une constante publique ou d’un membre d’énumération**

- ❌ **interdite : modification du type d’une propriété, d’un champ, d’un paramètre ou d’une valeur de retour**

- ❌ **interdite : ajout, suppression ou modification de l’ordre des paramètres**

- ❌ **interdite : ajout ou suppression du mot clé [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) ou [ref](../../csharp/language-reference/keywords/ref.md) d’un paramètre**

- ❌ **interdite : modification du nom d’un paramètre (y compris la modification de sa casse)**

  Cela est considéré comme un changement cassant pour deux raisons :

  - Cela empêche les scénarios à liaison tardive comme la fonctionnalité de liaison tardive de Visual Basic et [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) de C#.

  - Cela annule la [compatibilité de la source](categories.md#source-compatibility) lorsque les développeurs utilisent des [arguments nommés](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- ❌ **interdite : passage d’une valeur de retour `ref` à une valeur de retour `ref readonly`**

- ❌️ **interdite : la modification d’un `ref readonly` en `ref` valeur de retour sur une méthode virtuelle ou une interface**

- ❌ **interdite : ajout ou suppression d’un [abstract](../../csharp/language-reference/keywords/abstract.md) d’un membre**

- ❌ **interdite : suppression du mot clé [virtuel](../../csharp/language-reference/keywords/virtual.md) d’un membre**

  Bien que cela n’est souvent pas un changement cassant, car le compilateur C# a tendance à émettre des instructions [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) en langage intermédiaire pour appeler des méthodes non virtuelles (`callvirt` effectue une vérification de valeur null, alors qu’un appel normal ne le fait pas), ce comportement n’est pas invariable pour plusieurs raisons :
  - C# n’est pas le seul langage que .NET cible.

  - Le compilateur C# essaie progressivement d’optimiser `callvirt` en un appel normal chaque fois que la méthode cible est non virtuelle et n’a probablement pas la valeur null (par exemple une méthode accessible via [l’opérateur de propagation de NULL ?](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Rendre une méthode virtuelle signifie que le code consommateur finirait souvent par l’appeler de façon non virtuelle.

- ❌ **interdite : ajout du mot clé [Virtual](../../csharp/language-reference/keywords/virtual.md) à un membre**

- ❌ **interdite : création d’un membre virtuel abstract**

  Un [membre virtuel](../../csharp/language-reference/keywords/virtual.md) fournit une implémentation de méthode qui *peut être* substituée par une classe dérivée. Un [membre abstrait](../../csharp/language-reference/keywords/abstract.md) ne fournit aucune implémentation et *doit être* substitué.

- ❌ **interdite : ajout d’un membre abstrait à un type public qui a des constructeurs accessibles (publics ou protégés) et qui n’est pas [sealed](../../csharp/language-reference/keywords/sealed.md)**

- ❌ **interdite : ajout ou suppression du mot clé [statique](../../csharp/language-reference/keywords/static.md) d’un membre**

- ❌ **interdite : ajout d’une surcharge qui exclut une surcharge existante et définit un comportement différent**

  Cela empêche de fonctionner les clients existants qui étaient liés à la surcharge précédente. Par exemple, si une classe a une seule version d’une méthode qui accepte un <xref:System.UInt32>, un consommateur existant est correctement lié à cette surcharge lors du passage d’une valeur <xref:System.Int32>. Toutefois, si vous ajoutez une surcharge qui accepte un <xref:System.Int32> lors de la recompilation ou à l’aide d’une liaison tardive, le compilateur est maintenant lié à la nouvelle surcharge. Si un comportement différent se produit, il s’agit d’un changement cassant.

- ❌ **interdite : ajout d’un constructeur à une classe qui n’avait précédemment aucun constructeur sans ajouter le constructeur sans paramètre**

- ❌️ **interdite : ajout de [ReadOnly](../../csharp/language-reference/keywords/readonly.md) à un champ**

- ❌ **interdite : réduction de la visibilité d’un membre**

   Cela inclut la réduction de la visibilité d’un membre [protégé](../../csharp/language-reference/keywords/protected.md) lorsqu’il y a des constructeurs *accessibles* (`public` ou `protected`) et que le type n’est *pas* [sealed](../../csharp/language-reference/keywords/sealed.md). Si ce n’est pas le cas, la réduction de la visibilité d’un membre protégé est autorisée.

   L’amélioration de la visibilité d’un membre est autorisée.

- ❌ **interdite : modification du type d’un membre**

   La valeur renvoyée d’une méthode ou le type d’une propriété ou d’un champ ne peut pas être modifiée. Par exemple, la signature d’une méthode qui retourne un <xref:System.Object> ne peut pas être modifiée afin de retourner un <xref:System.String>, ou vice versa.

- ❌ **interdite : ajout d’un champ à un struct qui n’avait précédemment aucun État**

  Les règles d’affectation autorisent l’utilisation de variables non initialisées tant que le type de variable est un struct sans état. Si le struct est avec état, le code pourrait se retrouver avec des données non initialisées. Il s’agit potentiellement d’un changement cassant binaire et d’un changement cassant source.

- ❌ **interdit : déclenchement d’un événement existant lorsqu’il n’a jamais été déclenché**

## <a name="behavioral-changes"></a>Changements de comportement

### <a name="assemblies"></a>Assemblys

- ✔️ **autorisé : rendre un assembly portable quand les mêmes plateformes sont toujours prises en charge**

- ❌ **interdite : modification du nom d’un assembly**
- ❌ **interdite : modification de la clé publique d’un assembly**

### <a name="properties-fields-parameters-and-return-values"></a>Propriétés, champs, paramètres et valeurs renvoyées

- ✔️ **autorisé : modification de la valeur d’une propriété, d’un champ, d’une valeur de retour ou d’un paramètre de [sortie](../../csharp/language-reference/keywords/out-parameter-modifier.md) en un type plus dérivé**

  Par exemple, une méthode qui retourne un type <xref:System.Object> peut retourner une instance de <xref:System.String>. (Toutefois, la signature de méthode ne peut pas être modifiée).

- ✔️ **autorisé : l’extension de la plage de valeurs acceptées pour une propriété ou un paramètre si le membre n’est pas [virtuel](../../csharp/language-reference/keywords/virtual.md)**

  Alors que la plage de valeurs qui peuvent être passées à la méthode ou qui sont retournées par le membre peut être développée, le paramètre ou le type de membre ne peut pas. Par exemple, tandis que les valeurs passées à une méthode peuvent s’étendre de 0-124 à 0-255, le type de paramètre ne peut pas être changé de <xref:System.Byte> à <xref:System.Int32>.

- ❌ **interdite : l’extension de la plage de valeurs acceptées pour une propriété ou un paramètre si le membre est [virtuel](../../csharp/language-reference/keywords/virtual.md)**

   Ce changement empêche le fonctionnement des membres substitués existants, qui ne fonctionneront pas correctement pour la plage de valeurs étendue.

- ❌ **interdite : diminution de la plage de valeurs acceptées pour une propriété ou un paramètre**

- ❌ **interdite : l’extension de la plage des valeurs retournées pour une propriété, un champ, une valeur de retour ou un paramètre de [sortie](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- ❌ **interdite : modification des valeurs retournées d’une propriété, d’un champ, d’une valeur de retour de méthode ou d’un paramètre de [sortie](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- ❌ **interdite : modification de la valeur par défaut d’une propriété, d’un champ ou d’un paramètre**

- ❌ **interdite : modification de la précision d’une valeur de retour numérique**

- ❓ **Nécessite un jugement : une modification de l’analyse de l’entrée et la levée de nouvelles exceptions (même si le comportement de l’analyse n’est pas spécifié dans la documentation** )

### <a name="exceptions"></a>Exceptions

- ✔️ **autorisé : levée d’une exception plus dérivée qu’une exception existante**

  Étant donné que la nouvelle exception est une sous-classe d’une exception existante, le code de gestion des exceptions précédent continue à gérer l’exception. Par exemple, dans .NET Framework 4, les méthodes de création et de récupération de culture ont commencé à lever un <xref:System.Globalization.CultureNotFoundException> au lieu d’un <xref:System.ArgumentException> si la culture est introuvable. Étant donné que <xref:System.Globalization.CultureNotFoundException> dérive de <xref:System.ArgumentException>, il s’agit d’une modification acceptable.

- ✔️ **autorisées : la levée d’une exception plus spécifique que <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**

- ✔️ **autorisé : levée d’une exception considérée comme irrécupérable**

  Les exceptions irrécupérables ne doivent pas être interceptées, mais plutôt être gérées par un gestionnaire fourre-tout de haut niveau. Par conséquent, les utilisateurs ne sont pas censés avoir du code qui intercepte les exceptions explicites. Les exceptions irrécupérables sont :

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **autorisé : levée d’une nouvelle exception dans un nouveau chemin d’accès de code**

  L’exception doit s’appliquer uniquement à un nouveau chemin d’accès de code qui est exécuté avec les nouvelles valeurs de paramètre ou l’État et qui ne peut pas être exécuté par du code existant qui cible la version précédente.

- ✔️ **autorisé : suppression d’une exception pour activer un comportement plus robuste ou de nouveaux scénarios**

  Par exemple, une méthode `Divide` qui pouvait auparavant uniquement gérer des valeurs positives et levait un <xref:System.ArgumentOutOfRangeException> peut être modifiée pour prendre en charge les valeurs positives et négatives sans lever d’exception.

- ✔️ **autorisé : modification du texte d’un message d’erreur**

  Les développeurs ne doivent pas compter sur le texte des messages d’erreur, qui changent également selon la culture de l’utilisateur.

- ❌ **interdite : levée d’une exception dans tout autre cas non listé ci-dessus**

- ❌ **interdite : suppression d’une exception dans tout autre cas non listé ci-dessus**

### <a name="attributes"></a>Attributs

- ✔️ **autorisé : modification de la valeur d’un attribut qui n’est *pas* observable**

- ❌ **interdite : modification de la valeur d’un attribut observable**

- ❓ **Nécessite un jugement : suppression d’un attribut**

  Dans la plupart des cas, la suppression d’un attribut (comme <xref:System.NonSerializedAttribute>) est un changement cassant.

## <a name="platform-support"></a>Plateforme prise en charge

- ✔️ **autorisé : prise en charge d’une opération sur une plateforme qui n’était pas prise en charge précédemment**

- ❌ interdite **: ne prend pas en charge ou ne nécessite pas à présent un service pack spécifique pour une opération précédemment prise en charge sur une plateforme**

## <a name="internal-implementation-changes"></a>Modifications de l’implémentation interne

- ❓ **Nécessite un jugement : modification de la surface d’exposition d’un type interne**

   Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas, où les bibliothèques tierces les plus courantes ou un grand nombre de développeurs dépendent d’API internes, ces modifications ne peuvent pas être autorisées.

- ❓ **Nécessite un jugement : modification de l’implémentation interne d’un membre**

  Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas où le code du client dépend souvent de la réflexion privée ou où la modification introduit des effets secondaires involontaires, ces modifications peuvent ne pas être autorisées.

- ✔️ **autorisées : amélioration des performances d’une opération**

   La possibilité de modifier les performances d’une opération est essentielle, mais ces modifications peuvent endommager le code repose sur la vitesse actuelle d’une opération. Cela est particulièrement vrai pour du code qui dépend de la chronologie des opérations asynchrones. La modification des performances ne doit avoir aucun effet sur d’autres comportements de l’API en question ; dans le cas contraire, la modification sera arrêtée.

- ✔️ **autorisées : en modifiant indirectement (et souvent défavorablement) les performances d’une opération**

  Si la modification en question n’est pas considérée comme un changement cassant pour une raison quelconque, cela est acceptable. Souvent, des mesures doivent être prises, ce qui peut inclure des opérations supplémentaires ou l’ajout de nouvelles fonctionnalités. Cela affectera presque toujours les performances, mais peut s’avérer essentiel pour que l’API en question fonctionne comme prévu.

- ❌ **interdite : modification d’une API synchrone en asynchrone (et inversement)**

## <a name="code-changes"></a>Modifications du code

- ✔️ **autorisé : ajout de [paramètres](../../csharp/language-reference/keywords/params.md) à un paramètre**

- ❌ **interdite : modification d’un [struct](../../csharp/language-reference/builtin-types/struct.md) en [classe](../../csharp/language-reference/keywords/class.md) et vice versa**

- ❌ **interdite : ajout du mot clé [checked](../../csharp/language-reference/keywords/virtual.md) à un bloc de code**

   Cette modification peut pousser le code précédemment exécuté à lever <xref:System.OverflowException>, ce qui n’est pas acceptable.

- ❌ **interdite : suppression des [paramètres](../../csharp/language-reference/keywords/params.md) d’un paramètre**

- ❌ **interdite : modification de l’ordre dans lequel les événements sont déclenchés**

  Les développeurs peuvent raisonnablement s’attendre à ce que les événements se déclenchent dans le même ordre, et le code développeur dépend souvent de l’ordre dans lequel les événements sont déclenchés.

- ❌ **interdite : suppression du déclenchement d’un événement sur une action donnée**

- ❌ **interdite : modification du nombre d’appels des événements donnés**

- ❌ **interdite : ajout du <xref:System.FlagsAttribute> à un type énumération**
