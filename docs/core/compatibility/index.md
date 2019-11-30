---
title: Types de modifications avec rupture-.NET Core
description: Découvrez comment .NET Core tente de maintenir la compatibilité pour les développeurs sur les versions de .NET et quel type de modification est considéré comme une modification avec rupture.
ms.date: 06/10/2019
ms.openlocfilehash: 5624a35a0d71224faf9adc5df2b02a529e650314
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567718"
---
# <a name="changes-that-affect-compatibility"></a>Modifications qui affectent la compatibilité

Tout au long de son histoire, .NET a tenté de maintenir un niveau élevé de compatibilité de version en version et entre les différentes déclinaisons de .NET. Cette philosophie s’applique toujours avec .NET Core. Bien que .NET Core peut être considéré comme une nouvelle technologie indépendante du .NET Framework, deux facteurs majeurs limitent la capacité de .NET Core à diverger du .NET Framework :

- Un grand nombre de développeurs ont développé à la base ou continuent à développer des applications .NET Framework. Ils s’attendent à un comportement cohérent entre les implémentations de .NET.

- Les projets de bibliothèque .NET Standard permettent aux développeurs de créer des bibliothèques qui ciblent les API communes partagées par .NET Core et .NET Framework. Les développeurs s’attendent à ce qu’une bibliothèque utilisée dans une application .NET Core se comporte comme la bibliothèque utilisée dans une application .NET Framework.

En plus de la compatibilité entre les implémentations de .NET, les développeurs s’attendent à un haut niveau de compatibilité entre les versions de .NET Core. En particulier, le code écrit pour une version antérieure de .NET Core doit s’exécuter sans problème sur une version ultérieure de .NET Core. En fait, de nombreux développeurs s’attendent à ce que les nouvelles API dans les dernières versions de .NET Core soient également compatibles avec les versions préliminaires dans lesquelles ces API ont été introduites.

Cet article décrit les catégories de modifications de compatibilité (ou changements cassants) et la manière dont l’équipe .NET évalue les modifications dans chacune de ces catégories. Comprendre comment l’équipe .NET approche des modifications avec rupture possibles est particulièrement utile pour les développeurs qui ouvrent des requêtes de tirage dans le référentiel GitHub [dotnet/corefx](https://github.com/dotnet/corefx) qui modifient le comportement des API existantes.

> [!NOTE]
> Pour une définition des catégories de compatibilité, comme la compatibilité binaire et la compatibilité descendante, consultez [Catégories de changements cassants](categories.md).

Les sections suivantes décrivent les catégories de modifications apportées aux API .NET Core et leur impact sur la compatibilité des applications. L’icône ✔️ indique qu’un type particulier de modification est autorisé, ❌ indique qu’elle n’est pas autorisée et ❓ indique une modification qui peut ou non être autorisée. Les modifications de cette dernière catégorie nécessitent un jugement et une évaluation de la prédiction, évidente et cohérente du comportement précédent.

> [!NOTE]
> En plus de servir de guide pour l’évaluation des modifications apportées aux bibliothèques .NET Core, les développeurs de bibliothèques peuvent également utiliser ces critères pour évaluer les modifications apportées à leurs bibliothèques qui ciblent plusieurs implémentations et versions de .NET.

## <a name="modifications-to-the-public-contract"></a>Modifications au contrat public

Les modifications de cette catégorie modifient la surface d’exposition publique d’un type. La plupart des modifications de cette catégorie ne sont pas autorisées dans la mesure où elles enfreignent une *compatibilité descendante* (la possibilité pour une application qui a été développée avec une version précédente d’une API de s’exécuter sans recompilation sur une version ultérieure).

### <a name="types"></a>Types

- **✔️ La suppression d’une implémentation d’interface d’un type de l’interface est déjà implémentée par un type de base️**

- **❓ Ajout d’une nouvelle implémentation d’interface à un type**

  Il s’agit d’une modification acceptable, car elle n’affectera pas les clients existants. Toutes les modifications au type doivent fonctionner dans les limites des modifications acceptables définies ici pour la nouvelle implémentation afin de rester acceptables. Une prudence extrême est nécessaire lors de l’ajout d’interfaces qui affectent directement la capacité d’un concepteur ou sérialiseur à générer du code ou des données qui ne peuvent pas être consommées à un bas niveau. Par exemple, l’interface <xref:System.Runtime.Serialization.ISerializable>.

- **❓ Ajout d’une classe de base**

  Un type peut être introduit dans une hiérarchie entre deux types existants si elle n’introduit pas de nouveaux membres [abstraits](../../csharp/language-reference/keywords/abstract.md) et ne modifie pas la sémantique ou le comportement des types existants. Par exemple, dans .NET Framework 2.0, la classe <xref:System.Data.Common.DbConnection> est devenue une classe de base pour <xref:System.Data.SqlClient.SqlConnection>, qui était précédemment dérivée directement de <xref:System.ComponentModel.Component>.

- **✔️ Déplacement d’un type d’un assembly à un autre**

  Notez que *l’ancien* assembly doit être marqué avec le <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> qui pointe vers le nouvel assembly.

- **✔️ Changement d’un type [struct](../../csharp/language-reference/keywords/struct.md) en type `readonly struct`**

  Notez que le changement d’un type `readonly struct` en type `struct` n’est pas autorisé.

- **✔️ L’ajout du mot clé [sealed](../../csharp/language-reference/keywords/sealed.md) ou [abstraite](../../csharp/language-reference/keywords/abstract.md) à un type lorsqu’il y a aucun constructeur *accessible* (public ou protégé)**

- **✔️ Extension de la visibilité d’un type**

- **❌ modification de l’espace de noms ou du nom d’un type**

- **❌ renommer ou supprimer un type public**

   Cela empêche tout code qui utilise le type renommé ou supprimé de fonctionner.

- **❌ modification du type sous-jacent d’une énumération**

   Il s’agit d’un changement cassant au niveau de la compilation et du comportement ainsi qu’un changement cassant binaire qui peut rendre les arguments d’attribut non analysables.

- **❌ sceller un type qui a été précédemment non scellé**

- **❌ ajout d’une interface à l’ensemble des types de base d’une interface**

   Si une interface implémente une interface qu’elle n’implémentait pas précédemment, tous les types implémentant la version d’origine de l’interface cessent de fonctionner.

- **❓ Suppression d’une classe d’un ensemble des classes de base ou d’une interface à partir de l’ensemble des interfaces implémentées**

  Il existe une exception à la règle pour la suppression de l’interface : vous pouvez ajouter l’implémentation d’une interface qui dérive de l’interface supprimée. Par exemple, vous pouvez supprimer <xref:System.IDisposable> si le type ou l’interface implémente désormais <xref:System.ComponentModel.IComponent>, qui implémente <xref:System.IDisposable>.

- **❌ la modification d’un type de `readonly struct` en type [struct](../../csharp/language-reference/keywords/struct.md)**

  Notez que le changement d’un type `struct` en type `readonly struct` est autorisé.

- **❌ la modification d’un type [struct](../../csharp/language-reference/keywords/struct.md) en type `ref struct`, et vice versa**

- **❌ réduire la visibilité d’un type**

   Toutefois, l’augmentation de la visibilité d’un type est autorisée.

### <a name="members"></a>Membres

- **✔️ Développement de la visibilité d’un membre qui n’est pas [virtual](../../csharp/language-reference/keywords/sealed.md)**

- **✔ Ajout d’un membre abstrait à un type public qui n’a pas de constructeur️ *accessible* (public ou protégé) ou dont le type est [sealed](../../csharp/language-reference/keywords/sealed.md)**

  Toutefois, l’ajout à un membre abstrait à un type qui a des constructeurs accessibles (publics ou protégés) et n’est pas `sealed` n’est pas autorisé.

- **✔️ Restriction de la visibilité d’un membre [protected](../../csharp/language-reference/keywords/protected.md) chaque fois que le type n’a pas de constructeur accessible (public ou protégé) ou que le type est [sealed](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Déplacement d’un membre vers une classe supérieure au type à partir duquel il a été supprimé dans la hiérarchie**

- **✔️ Ajout ou suppression d’une substitution**

  Notez qu’en cas d’ajout d’une substitution, les consommateurs précédents pourraient ignorer la substitution lors de l’appel de [base](../../csharp/language-reference/keywords/base.md).

- **✔️ l’ajout d’un constructeur à une classe, avec un constructeur sans paramètre si la classe n’avait pas précédemment de constructeurs**

   Cependant, ajouter un constructeur à une classe qui n’avait auparavant aucun constructeur *sans* ajouter le constructeur sans paramètre n’est pas autorisé.

- **✔ Changement d’un membre de️ [abstract](../../csharp/language-reference/keywords/abstract.md) à [virtual](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ Changement d’une valeur renvoyée `ref readonly` à `ref` (à l’exception des méthodes virtuelles et des interfaces)**

- **✔️ Suppression d’un [readonly](../../csharp/language-reference/keywords/readonly.md) d’un champ, sauf si le type statique du champ est un type valeur mutable**

- **✔️ Appel d’un nouvel événement qui n’a pas été défini précédemment**

- **❓ Ajout d’un nouveau champ d’instance à un type**

   Cette modification a un impact sur la sérialisation.

- **❌ renommer ou supprimer un membre ou un paramètre public**

   Cela empêche tout code qui utilise le membre ou paramètre renommé ou supprimé de fonctionner.

   Notez que cela inclut la suppression et le changement de nom d’un accesseur Get ou Set à partir d’une propriété, ou de membres d’une énumération.

- **❌ ajout d’un membre à une interface**

- **❌ modification de la valeur d’une constante publique ou d’un membre d’énumération**

- **❌ la modification du type d’une propriété, d’un champ, d’un paramètre ou d’une valeur de retour**

- **❌ de l’ajout, de la suppression ou de la modification de l’ordre des paramètres**

- **❌ de l’ajout ou de la suppression du mot clé [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) ou [ref](../../csharp/language-reference/keywords/ref.md) d’un paramètre**

- **❌ le changement de nom d’un paramètre (y compris la modification de sa casse)**

  Cela est considéré comme un changement cassant pour deux raisons :

  - Cela empêche les scénarios à liaison tardive comme la fonctionnalité de liaison tardive de Visual Basic et [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) de C#.

  - Cela annule la [compatibilité de la source](categories.md#source-compatibility) lorsque les développeurs utilisent des [arguments nommés](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- **❌ de la modification d’une valeur de retour de `ref` en une valeur de retour `ref readonly`**

- **❌️ la modification d’un `ref readonly` en valeur de retour `ref` sur une méthode ou une interface virtuelle**

- **❌ de l’ajout ou de la suppression d’une [abstraite](../../csharp/language-reference/keywords/abstract.md) d’un membre**

- **❌ de la suppression du mot clé [Virtual](../../csharp/language-reference/keywords/virtual.md) d’un membre**

  Bien que cela n’est souvent pas un changement cassant, car le compilateur C# a tendance à émettre des instructions [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) en langage intermédiaire pour appeler des méthodes non virtuelles (`callvirt` effectue une vérification de valeur null, alors qu’un appel normal ne le fait pas), ce comportement n’est pas invariable pour plusieurs raisons :
  - C# n’est pas le seul langage que .NET cible.

  - Le compilateur C# essaie progressivement d’optimiser `callvirt` en un appel normal chaque fois que la méthode cible est non virtuelle et n’a probablement pas la valeur null (par exemple une méthode accessible via [l’opérateur de propagation de NULL ?](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Rendre une méthode virtuelle signifie que le code consommateur finirait souvent par l’appeler de façon non virtuelle.

- **❌ l’ajout du mot clé [Virtual](../../csharp/language-reference/keywords/virtual.md) à un membre**

- **❌ la création d’un membre virtuel abstract**

  Un [membre virtuel](../../csharp/language-reference/keywords/virtual.md) fournit une implémentation de méthode qui *peut être* substituée par une classe dérivée. Un [membre abstrait](../../csharp/language-reference/keywords/abstract.md) ne fournit aucune implémentation et *doit être* substitué.

- **❌ l’ajout d’un membre abstrait à un type public qui a des constructeurs accessibles (publics ou protégés) et qui n’est pas [sealed](../../csharp/language-reference/keywords/sealed.md)**

- **❌ de l’ajout ou de la suppression du mot clé [static](../../csharp/language-reference/keywords/static.md) d’un membre**

- **❌ ajout d’une surcharge qui exclut une surcharge existante et définit un comportement différent**

  Cela empêche de fonctionner les clients existants qui étaient liés à la surcharge précédente. Par exemple, si une classe a une seule version d’une méthode qui accepte un <xref:System.UInt32>, un consommateur existant est correctement lié à cette surcharge lors du passage d’une valeur <xref:System.Int32>. Toutefois, si vous ajoutez une surcharge qui accepte un <xref:System.Int32> lors de la recompilation ou à l’aide d’une liaison tardive, le compilateur est maintenant lié à la nouvelle surcharge. Si un comportement différent se produit, il s’agit d’un changement cassant.

- **❌ ajout d’un constructeur à une classe qui n’avait précédemment aucun constructeur sans ajouter le constructeur sans paramètre**

- **❌️ l’ajout de [ReadOnly](../../csharp/language-reference/keywords/readonly.md) à un champ**

- **❌ réduire la visibilité d’un membre**

   Cela inclut la réduction de la visibilité d’un membre [protected](../../csharp/language-reference/keywords/protected.md) lorsqu’il y a des constructeurs *accessibles* (publics ou protégés) et que le type n’est *pas* [sealed](../../csharp/language-reference/keywords/sealed.md). Si ce n’est pas le cas, la réduction de la visibilité d’un membre protégé est autorisée.

   Notez que l’augmentation de la visibilité d’un membre est autorisée.

- **❌ modification du type d’un membre**

   La valeur renvoyée d’une méthode ou le type d’une propriété ou d’un champ ne peut pas être modifiée. Par exemple, la signature d’une méthode qui retourne un <xref:System.Object> ne peut pas être modifiée afin de retourner un <xref:System.String>, ou vice versa.

- **❌ l’ajout d’un champ à un struct qui n’avait précédemment aucun État**

  Les règles d’affectation autorisent l’utilisation de variables non initialisées tant que le type de variable est un struct sans état. Si le struct est avec état, le code pourrait se retrouver avec des données non initialisées. Il s’agit potentiellement d’un changement cassant binaire et d’un changement cassant source.

- **❌ déclenchant un événement existant lorsqu’il n’a jamais été déclenché avant**

## <a name="behavioral-changes"></a>Changements de comportement

### <a name="assemblies"></a>Assemblies

- **✔️ Rendre un assembly portable lorsque les mêmes plateformes sont toujours prises en charge**

- **❌ modification du nom d’un assembly**
- **❌ modification de la clé publique d’un assembly**

### <a name="properties-fields-parameters-and-return-values"></a>Propriétés, champs, paramètres et valeurs renvoyées

- **✔️ Modification de la valeur d’une propriété, d’un champ, d’une valeur renvoyée, ou d’un paramètre [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) en un type plus dérivé**

  Par exemple, une méthode qui retourne un type <xref:System.Object> peut retourner une instance de <xref:System.String>. (Toutefois, la signature de méthode ne peut pas être modifiée).

- **✔️ Augmentation de l’intervalle accepté de valeurs pour une propriété ou un paramètre si le membre n’est pas [virtual](../../csharp/language-reference/keywords/virtual.md)**

  Notez que bien que la plage de valeurs qui peuvent être passées à la méthode ou sont retournées par le membre peut être étendue, le type de membre ou paramètre ne peut pas l’être. Par exemple, tandis que les valeurs passées à une méthode peuvent s’étendre de 0-124 à 0-255, le type de paramètre ne peut pas être changé de <xref:System.Byte> à <xref:System.Int32>.

- **❌ l’extension de la plage de valeurs acceptées pour une propriété ou un paramètre si le membre est [virtuel](../../csharp/language-reference/keywords/virtual.md)**

   Ce changement empêche le fonctionnement des membres substitués existants, qui ne fonctionneront pas correctement pour la plage de valeurs étendue.

- **❌ diminuant la plage de valeurs acceptées pour une propriété ou un paramètre**

- **❌ l’extension de la plage de valeurs retournées pour une propriété, un champ, une valeur de retour ou un paramètre de [sortie](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- **❌ la modification des valeurs retournées d’une propriété, d’un champ, d’une valeur de retour de méthode ou d’un paramètre de [sortie](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- **❌ modification de la valeur par défaut d’une propriété, d’un champ ou d’un paramètre**

- **❌ modification de la précision d’une valeur de retour numérique**

- **❓ Changement dans l’analyse de l’entrée et levée de nouvelles exceptions (même si le comportement d’analyse n’est pas spécifié dans la documentation)**

### <a name="exceptions"></a>Exceptions

- **✔️ Levée d’une exception plus dérivée qu’une exception existante**

  Étant donné que la nouvelle exception est une sous-classe d’une exception existante, le code de gestion des exceptions précédent continue à gérer l’exception. Par exemple, dans .NET Framework 4, les méthodes de création et de récupération de culture ont commencé à lever un <xref:System.Globalization.CultureNotFoundException> au lieu d’un <xref:System.ArgumentException> si la culture est introuvable. Étant donné que <xref:System.Globalization.CultureNotFoundException> dérive de <xref:System.ArgumentException>, il s’agit d’une modification acceptable.

- **✔️ Levée d’une exception plus spécifique que <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**

- **✔️ Levée d’une exception qui est considérée comme irrécupérable**

  Les exceptions irrécupérables ne doivent pas être interceptées, mais plutôt être gérées par un gestionnaire fourre-tout de haut niveau. Par conséquent, les utilisateurs ne sont pas censés avoir du code qui intercepte les exceptions explicites. Les exceptions irrécupérables sont :

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ Levée une exception dans un nouveau chemin de code**

  L’exception doit s’appliquer uniquement à un nouveau chemin de code qui est exécuté avec les nouvelles valeurs de paramètre ou le nouvel état, et qui ne peut pas être exécuté par le code existant qui cible la version précédente.

- **✔ Suppression d’une exception pour permettre un comportement plus robuste ou de nouveaux scénarios️**

  Par exemple, une méthode `Divide` qui pouvait auparavant uniquement gérer des valeurs positives et levait un <xref:System.ArgumentOutOfRangeException> peut être modifiée pour prendre en charge les valeurs positives et négatives sans lever d’exception.

- **✔️ Modification du texte d’un message d’erreur**

  Les développeurs ne doivent pas compter sur le texte des messages d’erreur, qui changent également selon la culture de l’utilisateur.

- **❌ levant une exception dans tout autre cas non listé ci-dessus**

- **❌ de la suppression d’une exception dans tout autre cas non listé ci-dessus**

### <a name="attributes"></a>Attributs

- **✔️ Modification de la valeur d’un attribut qui n’est *pas* observable**

- **❌ modification de la valeur d’un attribut *observable***

- **❓ Suppression d’un attribut**

  Dans la plupart des cas, la suppression d’un attribut (comme <xref:System.NonSerializedAttribute>) est un changement cassant.

## <a name="platform-support"></a>Plateforme prise en charge

- **✔️ Prise en charge d’une opération sur une plateforme qui n’était précédemment pas prise en charge**

- **❌ ne prend pas en charge ou ne nécessite pas une Service Pack spécifique pour une opération précédemment prise en charge sur une plateforme**

## <a name="internal-implementation-changes"></a>Modifications de l’implémentation interne

- **❓ Modification de la surface d’exposition d’un type interne**

   Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas, où les bibliothèques tierces les plus courantes ou un grand nombre de développeurs dépendent d’API internes, ces modifications ne peuvent pas être autorisées.

- **❓ Modification de l’implémentation interne d’un membre**

  Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas où le code du client dépend souvent de la réflexion privée ou où la modification introduit des effets secondaires involontaires, ces modifications peuvent ne pas être autorisées.

- **✔ Amélioration des performances d’une opération**

   La possibilité de modifier les performances d’une opération est essentielle, mais ces modifications peuvent endommager le code repose sur la vitesse actuelle d’une opération. Cela est particulièrement vrai pour du code qui dépend de la chronologie des opérations asynchrones. Notez que la modification de performances ne doit avoir aucun effet sur les autres comportements de l’API en question ; sinon, la modification sera un changement cassant.

- **✔️ Changement indirect (et souvent avec un impact négatif) des performances d’une opération**

  Si la modification en question n’est pas considérée comme un changement cassant pour une raison quelconque, cela est acceptable. Souvent, des mesures doivent être prises, ce qui peut inclure des opérations supplémentaires ou l’ajout de nouvelles fonctionnalités. Cela affectera presque toujours les performances, mais peut s’avérer essentiel pour que l’API en question fonctionne comme prévu.

- **❌ la modification d’une API synchrone en asynchrone (et inversement)**

## <a name="code-changes"></a>Modifications du code

- **✔️ Ajout de [params](../../csharp/language-reference/keywords/params.md) à un paramètre**

- **❌ la modification d’un [struct](../../csharp/language-reference/keywords/struct.md) en [classe](../../csharp/language-reference/keywords/class.md) et vice versa**

- **❌ l’ajout du mot clé [checked](../../csharp/language-reference/keywords/virtual.md) à un bloc de code**

   Cette modification peut pousser le code précédemment exécuté à lever <xref:System.OverflowException>, ce qui n’est pas acceptable.

- **❌ la suppression des [paramètres](../../csharp/language-reference/keywords/params.md) d’un paramètre**

- **❌ modification de l’ordre dans lequel les événements sont déclenchés**

  Les développeurs peuvent raisonnablement s’attendre à ce que les événements se déclenchent dans le même ordre, et le code développeur dépend souvent de l’ordre dans lequel les événements sont déclenchés.

- **❌ de la suppression du déclenchement d’un événement sur une action donnée**

- **❌ la modification du nombre de fois où les événements sont appelés**

- **❌ l’ajout du <xref:System.FlagsAttribute> à un type énumération**
