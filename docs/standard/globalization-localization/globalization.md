---
title: Globalisation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
ms.openlocfilehash: 1055b10d0e3e971a6b0963c1ed950fef903ac5bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239948"
---
# <a name="globalization"></a>Globalisation

La globalisation a trait à la conception et au développement d’applications universelles qui prennent en charge les interfaces localisées et les données régionales pour les utilisateurs de diverses cultures. Avant d’entreprendre la phase de conception, vous devez déterminer les cultures que votre application devra prendre en charge. Bien qu’une application cible par défaut une seule et même culture ou région, vous pouvez la concevoir et l’écrire de façon à faciliter son extension à d’autres cultures ou régions.

En tant que développeurs, nous avons tous des principes en matière d’interfaces utilisateur et des données qui sont formées par nos cultures. Par exemple, pour un développeur dont la langue est l’anglais des États-Unis, sérialiser les données de date et d’heure sous forme de chaîne au format `MM/dd/yyyy hh:mm:ss` semble tout à fait raisonnable. Cependant, la désérialisation de cette chaîne sur un système d’une autre culture est susceptible de lever une exception <xref:System.FormatException> ou de produire des données incorrectes. La globalisation nous permet d’identifier ces principes propres aux cultures et de s’assurer qu’elles n’affectent pas la conception ou le code de notre application.

Cet article expose certaines des questions phares que vous devez prendre en considération, ainsi que les bonnes pratiques que vous pouvez suivre pour gérer les chaînes, les valeurs de date et d’heure et les valeurs numériques dans une application globalisée.

## <a name="strings"></a>Chaînes

La gestion des caractères et des chaînes est un élément central de la globalisation, car chaque culture ou région peut utiliser des caractères et des jeux de caractères différents et les trier différemment. Cette section émet des recommandations pour l’utilisation de chaînes dans les applications globalisées.

### <a name="use-unicode-internally"></a>Utiliser Unicode en interne

Par défaut, .NET utilise des chaînes Unicode. Une chaîne Unicode se compose de zéro, un ou plusieurs objets <xref:System.Char>, chacun représentant une unité de code UTF-16. Il existe une représentation Unicode pour pratiquement tous les caractères de chaque jeu de caractères utilisé dans le monde.

Beaucoup d’applications et de systèmes d’exploitation, dont le système d’exploitation Windows, peuvent aussi utiliser des pages de codes pour représenter des jeux de caractères. Les pages de codes contiennent généralement les valeurs ASCII standard (de 0x00 à 0x7F) et mappent les autres caractères aux valeurs restantes (de 0x80 à 0xFF). L’interprétation des valeurs 0x80 à 0xFF dépend de la page de codes utilisée. C’est pour cette raison que vous devez éviter d’utiliser des pages de codes dans une application globalisée, dans la mesure du possible.

L’exemple suivant illustre les risques liés à l’interprétation des données de page de codes quand la page de codes par défaut d’un système est différente de celle sur lequel les données ont été enregistrées. (Pour simuler ce scénario, l’exemple spécifie explicitement des pages de codes différentes.) Tout d’abord, l’exemple définit un tableau qui se compose des caractères majuscules de l’alphabet grec. Ces caractères sont encodés dans un tableau d’octets en utilisant la page de codes 737 (aussi appelée MS-DOS Grec), tableau d’octets qui est ensuite enregistré dans un fichier. Si le fichier est récupéré et que son tableau d’octets est décodé en utilisant la page de codes 737, les caractères d’origine sont restaurés. En revanche, si le fichier est récupéré et que son tableau d’octets est décodé en utilisant la page de codes 1252 (ou Windows-1252, qui représente les caractères de l’alphabet latin), les caractères d’origine sont perdus.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

L’utilisation d’Unicode est la garantie que les mêmes unités de code correspondent toujours aux mêmes caractères, et que les mêmes caractères correspondent toujours aux mêmes tableaux d’octets.

### <a name="use-resource-files"></a>Utiliser les fichiers de ressources

Même si vous décidez de développer une application qui cible une seule et même culture ou région, vous avez tout intérêt à utiliser des fichiers de ressources pour y stocker les chaînes et les autres ressources qui s’afficheront dans l’interface utilisateur. Vous ne devez jamais les ajouter directement à votre code. L’utilisation de fichiers de ressources offre un certain nombre d’avantages :

- Toutes les chaînes se trouvent à un même emplacement. Vous n’avez pas besoin de parcourir tout le code source pour identifier les chaînes à modifier pour une langue ou une culture donnée.

- Il n’est pas nécessaire de dupliquer les chaînes. Souvent, les développeurs qui n’utilisent pas de fichiers de ressources définissent une même chaîne dans plusieurs fichiers de code source. Or, cette duplication augmente les chances d’oubli d’une ou plusieurs instances d’une chaîne modifiée.

- Au lieu de stocker les ressources qui ne sont pas des chaînes (p.ex., images ou données binaires) dans un fichier autonome, vous pouvez les inclure dans le fichier de ressources de façon à en faciliter la récupération.

L’utilisation de fichiers de ressources offre des avantages particuliers si vous créez une application localisée. Quand vous déployez des ressources dans des assemblys satellites, le common language runtime sélectionne automatiquement la ressource adaptée à la culture en fonction de la culture d’interface utilisateur active de l’utilisateur définie par la propriété <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>. Dans la mesure où vous fournissez une ressource appropriée propre à la culture et que vous instanciez correctement un objet <xref:System.Resources.ResourceManager> ou que vous utilisez une classe de ressource fortement typée, le runtime se charge de récupérer les ressources appropriées.

Pour plus d’informations sur la création de fichiers de ressources, consultez [Création de fichiers de ressources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Pour plus d’informations sur la création et le déploiement d’assemblys satellites, consultez [Création d'assemblys satellites](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) et [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Rechercher et comparer des chaînes

Dans la mesure du possible, vous devez traiter les chaînes comme des chaînes entières, et non comme une série de caractères individuels. Cela est particulièrement important quand il s’agit de trier ou rechercher des sous-chaînes de façon à éviter les problèmes liés à l’analyse de caractères combinés.

> [!TIP]
> Vous pouvez utiliser la classe <xref:System.Globalization.StringInfo> pour travailler sur les éléments de texte plutôt que sur les caractères individuels d’une chaîne.

Pendant les opérations de recherche et de comparaison de chaînes, l’erreur courante à éviter est de traiter les chaînes comme des ensembles de caractères, chacun représenté par un objet <xref:System.Char>. De fait, un même caractère peut être constitué d’un ou plusieurs objets <xref:System.Char>. Ces caractères se trouvent généralement dans des chaînes de cultures dont les alphabets comportent des caractères extérieurs à la plage de caractères latins de base Unicode (de U+0021 à U+007E). L’exemple suivant recherche l’index du caractère LETTRE MAJUSCULE LATINE A AVEC ACCENT GRAVE (U+00C 0) dans une chaîne. Toutefois, ce caractère peut être représenté de deux façons différentes : en tant qu’unité de code unique (U + 00C0) ou en tant que caractère composite (deux unités de code : U + 0041 et U + 0300). Dans ce cas, le caractère est représenté dans l’instance de chaîne par deux objets <xref:System.Char>, U + 0041 et U + 0300. L’exemple de code appelle les surcharges <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> et <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> pour rechercher la position de ce caractère dans l’instance de la chaîne, mais elles retournent des résultats différents. Le premier appel de méthode comporte un argument <xref:System.Char> ; il effectue une comparaison ordinale et ne peut donc pas trouver de correspondance. Le deuxième appel comporte un argument <xref:System.String> ; il effectue une comparaison dépendante de la culture et trouve donc une correspondance.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Vous pouvez lever une partie de l’ambiguïté de cet exemple (appel à deux surcharges similaires d’une méthode qui retourne des résultats différents) en appelant une surcharge qui inclue un paramètre <xref:System.StringComparison>, tel que la méthode <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ou <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.

Cependant, les recherches ne sont pas toujours dépendantes de la culture. Si la recherche vise à prendre une décision en matière de sécurité ou à autoriser ou interdire l’accès à une ressource, la comparaison doit être ordinale, comme nous le verrons dans la section suivante.

### <a name="test-strings-for-equality"></a>Tester l’égalité de chaînes

Si vous voulez effectuer un test d’égalité entre deux chaînes au lieu de les comparer par rapport à l’ordre de tri, utilisez la méthode <xref:System.String.Equals%2A?displayProperty=nameWithType> plutôt qu’une méthode de comparaison de chaînes comme <xref:System.String.Compare%2A?displayProperty=nameWithType> ou <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.

Les comparaisons d’égalité sont généralement effectuées pour accéder de manière conditionnelle à certaines ressources. Par exemple, vous pouvez effectuer une comparaison d’égalité pour vérifier un mot de passe ou confirmer qu’un fichier existe. Ces comparaisons non linguistiques doivent toujours être ordinales et non dépendantes de la culture. En général, vous avez tout intérêt à appeler la méthode d’instance <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ou la méthode statique <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> avec la valeur <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pour des chaînes telles que des mots de passe et la valeur <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pour des chaînes telles que des noms de fichiers ou des URI.

Les comparaisons d’égalité impliquent parfois des recherches ou des comparaisons de sous-chaînes plutôt que des appels à la méthode <xref:System.String.Equals%2A?displayProperty=nameWithType>. Dans certains cas, vous pouvez rechercher une sous-chaîne pour déterminer si elle est égale à une autre chaîne. Si l’objet de cette comparaison n’est pas linguistique, la recherche doit aussi être ordinale et non dépendante de la culture.

L’exemple suivant illustre le risque associé à une recherche dépendante de la culture sur des données non linguistiques. La méthode `AccessesFileSystem` vise à interdire l’accès au système de fichiers pour les URI commençant par la sous-chaîne « FILE». Pour cela, elle effectue une comparaison dépendante de la culture et sans respect de la casse entre le début de l’URI et la chaîne « FILE ». Sachant qu’un URI qui accède au système de fichiers peut commencer par « FILE: » ou « file: », la supposition implicite est que ce « i » (U+0069) est toujours l’équivalent en minuscule de « I » (U+0049). Toutefois, en turc et en azéri, la version en majuscule du « i » est « i » (U + 0130). Du fait de cette différence, la comparaison dépendante de la culture autorise l’accès au système de fichiers, alors qu’il devrait être interdit.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Vous pouvez éviter ce problème en effectuant une comparaison ordinale qui ignore la casse, comme le montre l’exemple suivant.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Ordonner et trier des chaînes

En règle générale, les chaînes ordonnées devant s’afficher dans l’interface utilisateur doivent être triées en fonction de la culture. La plupart du temps, ces comparaisons de chaînes sont gérées implicitement par .NET dès lors que vous appelez une méthode qui trie les chaînes, comme <xref:System.Array.Sort%2A?displayProperty=nameWithType> ou <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Par défaut, les chaînes sont triées selon les conventions de tri de la culture active. L’exemple suivant illustre la différence entre le tri d’un tableau de chaînes avec les conventions de la culture Anglais (États-Unis) et le tri de ce même tableau avec la culture Suédois (Suède).

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

La comparaison de chaînes dépendante de la culture est définie par l’objet <xref:System.Globalization.CompareInfo>, qui est retourné par la propriété <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> de chaque culture. Les comparaisons de chaînes dépendantes de la culture qui utilisent les surcharges de méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> utilisent aussi l’objet <xref:System.Globalization.CompareInfo>.

.NET utilise des tables pour effectuer des tris dépendants de la culture sur les données de chaîne. Le contenu de ces tables, qui comportent des données de pondération de tri et de normalisation de chaînes, est déterminé par la version de la norme Unicode implémentée par une version déterminée de .NET. Le tableau suivant répertorie les versions d’Unicode implémentées par les versions indiquées de .NET. Notez que cette liste de versions d’Unicode prises en charge s’applique uniquement à la comparaison et au tri de caractères ; elle ne s’applique pas à la classification des caractères Unicode par catégorie. Pour plus d’informations, consultez la section « Chaînes et norme Unicode » de l’article <xref:System.String>.

|Version du .NET Framework|Système d’exploitation|Version d’Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Tous les systèmes d'exploitation|Unicode 4.1|
|.NET Framework 3.0|Tous les systèmes d'exploitation|Unicode 4.1|
|.NET Framework 3.5|Tous les systèmes d'exploitation|Unicode 4.1|
|.NET Framework 4|Tous les systèmes d'exploitation|Unicode 5.0|
|.NET Framework 4.5 et ultérieur sur Windows 7|Unicode 5.0|
|.NET Framework 4.5 et ultérieur sur les systèmes d’exploitation Windows 8 et versions ultérieures|Unicode 6.3.0|
|.NET Core (toutes les versions)|En fonction de la version de la norme Unicode prise en charge par le système d’exploitation sous-jacent.|

Depuis .NET Framework 4.5 et dans toutes les versions de .NET Core, la comparaison et le tri de chaînes dépendent du système d’exploitation. .NET Framework 4.5 et ultérieur s’exécutant sur Windows 7 récupère les données dans ses propres tables qui implémentent Unicode 5.0. .NET Framework 4.5 et ultérieur s’exécutant sur Windows 8 récupère les données dans ses propres tables qui implémentent Unicode 6.3. Sur .NET Core, la version Unicode prise en charge dépend du système d’exploitation sous-jacent. Si vous sérialisez des données triées dépendantes de la culture, vous pouvez utiliser la classe <xref:System.Globalization.SortVersion> pour déterminer à quel moment vos données sérialisées doivent être triées de sorte qu’elles correspondent au .NET et à l’ordre de tri du système d’exploitation. Pour obtenir un exemple, consultez la rubrique relative à la classe <xref:System.Globalization.SortVersion>.

Si votre application effectue des tris étendus propres à la culture sur des données de chaîne, vous pouvez utiliser la classe <xref:System.Globalization.SortKey> pour comparer des chaînes. Une clé de tri reflète les pondérations de tri propres à la culture, notamment les pondérations alphabétiques, de casse et diacritiques d’une chaîne déterminée. Les comparaisons à base de clés de tri étant binaires, elles sont plus rapides que les comparaisons qui utilisent un objet <xref:System.Globalization.CompareInfo>, que ce soit de manière implicite ou explicite. Vous pouvez créer une clé de tri propre à la culture pour une chaîne déterminée en passant la chaîne à la méthode <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType>.

L’exemple suivant est similaire à l’exemple précédent. Cependant, au lieu d’appeler la méthode <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType>, qui appelle implicitement la méthode <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>, il définit une implémentation <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> qui compare les clés de tri, qu’il instancie et passe à la méthode <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Éviter la concaténation de chaînes

Dans la mesure du possible, évitez d’utiliser les chaînes composites qui sont construites au moment de l’exécution à partir d’expressions concaténées. Les chaînes composites sont difficiles à localiser, car elles prennent souvent en compte l’ordre grammatical de la langue d’origine de l’application qui ne s’applique pas aux autres langues localisées.

## <a name="handle-dates-and-times"></a>Gérer des dates et des heures

La façon dont vous gérez les valeurs de date et d’heure varie selon qu’elles s’affichent dans l’interface utilisateur ou qu’elles sont persistantes. Cette section se penche sur les deux cas. De même, elle explique comment gérer les décalages horaires et les opérations arithmétiques appliquées aux dates et heures.

### <a name="display-dates-and-times"></a>Afficher des dates et des heures

En règle générale, quand les dates et les heures s’affichent dans l’interface utilisateur, vous devez utiliser les conventions de mise en forme de la culture de l’utilisateur, ce qui est défini par la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> et l’objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété `CultureInfo.CurrentCulture.DateTimeFormat`. Les conventions de mise en forme de la culture active sont utilisées automatiquement quand vous mettez en forme une date en utilisant l’une de ces méthodes :

- méthode <xref:System.DateTime.ToString?displayProperty=nameWithType> sans paramètre ;

- méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, qui inclut une chaîne de format ;

- méthode <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> sans paramètre ;

- <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, qui inclut une chaîne de format ;

- fonctionnalité de [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md), quand elle est utilisée avec des dates.

L’exemple suivant affiche des données relatives au lever du soleil (« sunrise ») et au coucher du soleil (« sunset ») à deux reprises pour le 11 octobre 2012. Dans un premier temps, il définit la culture active Croate (Croatie), puis Anglais (Royaume-Uni). Dans les deux cas, les dates et heures s’affichent au format adapté à la culture en question.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Figer des dates et des heures

Vous ne devez jamais figer les données de date et d’heure dans un format qui peut varier d’une culture à une autre. Il s’agit d’une erreur de programmation courante qui se traduit par des données endommagées ou par une exception au moment de l’exécution. L’exemple suivant sérialise deux dates (le 9 janvier 2013 et le 18 août 2013) sous forme de chaînes en utilisant les conventions de mise en forme de la culture Anglais (États-Unis). Quand les données sont récupérées et analysées en utilisant les conventions de la culture Anglais (États-Unis), elles sont restaurées avec succès. En revanche, quand elles sont récupérées et analysées en utilisant les conventions de la culture Anglais (Royaume-Uni), la première date est interprétée par erreur comme étant le 1er septembre, et la deuxième ne peut pas être analysée, car le calendrier grégorien n’a pas de dix-huitième mois.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Vous pouvez éviter ce problème de l’une des trois façons suivantes :

- Sérialisez la date et l’heure au format binaire et non sous forme de chaîne.

- Enregistrez et analysez la représentation de la date et de l’heure sous la forme d’une chaîne de format personnalisé qui reste identique, quelle que soit la culture de l’utilisateur.

- Enregistrez la chaîne en utilisant les conventions de mise en forme de la culture dite indifférente.

L’exemple suivant illustre la dernière approche. Il utilise les conventions de mise en forme de la culture dite indifférente retournée par la propriété statique <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Prise en compte de la sérialisation et des fuseaux horaires

Une valeur de date et d’heure peut être interprétée de plusieurs façons, par exemple, en tant qu’heure générale (« les magasins seront ouverts le 2 janvier 2013 à 9h00 ») ou en tant que moment précis dans le temps (« Date de naissance : le 2 janvier 2013 à 6h32 »). Quand une valeur d’heure représente un moment précis dans le temps et que vous la restaurez à partir d’une valeur sérialisée, vous devez vérifier qu’elle représente le même moment dans le temps, quelle que soit la situation géographique ou le fuseau horaire de l’utilisateur.

L'exemple de code suivant illustre ce problème. Il enregistre une même valeur de date et d’heure locale sous forme de chaîne dans trois [formats standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) (« G » pour date générale et heure longue, « s » pour date/heure pouvant être triée et « o » pour date/heure aller-retour), ainsi qu’au format binaire.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Quand les données sont restaurées sur un système situé dans le même fuseau horaire que le système sur lequel elles ont été sérialisées, les valeurs de date et d’heure désérialisées sont le reflet exact de la valeur d’origine, comme le montre la sortie suivante :

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Cependant, si vous restaurez les données sur un système situé dans un autre fuseau horaire, seule la valeur de date et d’heure qui a été mise en forme avec la chaîne de format standard « o » (aller-retour) conserve les informations de fuseau horaire et par conséquent représente le même instant dans le temps. Voici le résultat de la restauration des données de date et d’heure sur un système situé dans le fuseau horaire d’Europe centrale :

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Pour représenter avec précision une valeur de date et d’heure qui correspond à un moment précis dans le temps, indépendamment du fuseau horaire du système sur lequel les données sont désérialisées, vous pouvez procéder de l’une des façons suivantes :

- Enregistrez la valeur sous forme de chaîne en utilisant la chaîne de format « o » (aller-retour). Ensuite, désérialisez-la sur le système cible.

- Convertissez-la au format UTC et enregistrez-la sous forme de chaîne en utilisant la chaîne de format standard « r » (RFC1123). Désérialisez-la ensuite sur le système cible et convertissez-la en heure locale.

- Convertissez-la au format UTC et enregistrez-la sous forme de chaîne en utilisant la chaîne de format standard « u » (universel pouvant être trié). Désérialisez-la ensuite sur le système cible et convertissez-la en heure locale.

- Convertissez-la au format UTC et enregistrez-la au format binaire. Désérialisez-la ensuite sur le système cible et convertissez-la en heure locale.

L’exemple suivant illustre chaque technique.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Quand les données sont sérialisées sur un système situé dans le fuseau horaire du Pacifique, puis désérialisées sur un système situé dans le fuseau horaire d’Europe centrale, l’exemple affiche la sortie suivante :

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Pour plus d’informations, consultez [Conversion d’heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Exécuter des calculs de date et d’heure

Les types <xref:System.DateTime> et <xref:System.DateTimeOffset> prennent en charge les opérations arithmétiques. Vous pouvez calculer la différence entre deux valeurs de date, ou vous pouvez ajouter ou soustraire des intervalles de temps déterminés à une valeur de date. Cependant, les opérations arithmétiques sur les valeurs de date et d’heure ne prennent pas en compte les fuseaux horaires et les règles d’ajustement de fuseaux horaires. Pour cette raison, les calculs arithmétiques sur les valeurs de date et d’heure qui représentent des moments dans le temps peuvent retourner des résultats incorrects.

Par exemple, le passage de l’heure d’hiver à l’heure d’été dans la zone Pacifique intervient le deuxième dimanche de mars, c’est-à-dire le 10 mars pour l’année 2013. Comme le montre l’exemple suivant, si vous calculez la date et l’heure à 48 heures après le 9 mars 2013 à 10h30 sur un système situé dans le fuseau horaire du Pacifique, le résultat (11 mars 2013 à 10h30) ne prend pas en compte le changement d’heure intervenu entre-temps

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Pour être certain qu’une opération arithmétique sur des valeurs de date et d’heure génère des résultats précis, procédez comme suit :

1. Convertissez l’heure du fuseau horaire source au format UTC.

2. Effectuez l’opération arithmétique.

3. Si le résultat obtenu est une valeur de date et d’heure, convertissez-la du format UTC à l’heure du fuseau horaire source.

L’exemple suivant est similaire à l’exemple précédent, sauf qu’il respecte ces trois étapes pour ajouter correctement 48 heures au 9 mars 2013 à 10h30.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Pour plus d’informations, consultez [Exécution d’opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Utiliser des noms dépendants de la culture pour les éléments de date

Votre application peut avoir besoin d’afficher le nom du mois ou le jour de la semaine. Pour cela, le code suivant est d’usage courant.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Or, ce code retourne toujours le nom des jours de la semaine en anglais. Il est fréquent que le code chargé d’extraire le nom du mois soit encore moins flexible. Il part souvent du principe que le calendrier est constitué de douze mois et affiche le nom des mois dans une langue spécifique.

En utilisant des [chaînes de format de date et d’heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ou les propriétés de l’objet <xref:System.Globalization.DateTimeFormatInfo>, il est facile d’extraire des chaînes qui correspondent au nom des jours de la semaine ou des mois dans la culture de l’utilisateur, comme l’illustre l’exemple suivant. Il remplace la culture active par la culture Français (France) et affiche le nom du jour de la semaine et le nom du mois pour le 1er juillet 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Valeurs numériques

La gestion des nombres varie selon qu’ils s’affichent dans l’interface utilisateur ou qu’ils sont persistants. Cette section se penche sur les deux cas.

> [!NOTE]
> Pendant les opérations d’analyse et de mise en forme, le .NET ne reconnaît comme caractères numériques que les caractères latins de base compris entre 0 à 9 (de U+0030 à U+0039).

### <a name="display-numeric-values"></a>Afficher des valeurs numériques

En règle générale, quand les nombres s’affichent dans l’interface utilisateur, vous devez utiliser les conventions de mise en forme de la culture de l’utilisateur, ce qui est défini par la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> et l’objet <xref:System.Globalization.NumberFormatInfo> retourné par la propriété `CultureInfo.CurrentCulture.NumberFormat`. Les conventions de mise en forme de la culture active sont utilisées automatiquement quand vous mettez en forme une date en utilisant l’une des méthodes suivantes :

- méthode `ToString` sans paramètre de tout type numérique ;

- méthode `ToString(String)` de tout type numérique, ce qui inclut une chaîne de format en guise d’argument ;

- fonctionnalité de [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md), quand elle est utilisée avec des valeurs numériques.

L’exemple suivant affiche la température moyenne par mois à Paris. Dans un premier temps, il définit la culture active Français (France) avant d’afficher les données, puis définit ensuite Anglais (États-Unis). Dans les deux cas, le nom des mois et les températures s’affichent au format adapté à la culture en question. À noter que les deux cultures utilisent des séparateurs décimaux différents dans la valeur de température. De même, notez que la chaîne de format de date et d’heure personnalisée « MMMM » est utilisée pour afficher le nom de mois complet et que la quantité d’espace nécessaire est allouée au nom de mois dans la chaîne de résultat par rapport à la longueur du nom de mois le plus long dans la tableau <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Conserver des valeurs numériques

Vous ne devez jamais conserver les données numériques dans un format propre à la culture. Il s’agit d’une erreur de programmation courante qui se traduit par des données endommagées ou par une exception au moment de l’exécution. L’exemple suivant génère dix nombres à virgule flottante aléatoires et les sérialise sous forme de chaînes en utilisant les conventions de mise en forme de la culture Anglais (États-Unis). Quand les données sont récupérées et analysées en utilisant les conventions de la culture Anglais (États-Unis), elles sont restaurées avec succès. Cependant, quand elles sont récupérées et analysées en utilisant les conventions de la culture Français (France), aucun de ces nombres ne peut être analysé, car les cultures utilisent des séparateurs décimaux différents.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Pour éviter ce problème, vous pouvez utiliser l’une de ces techniques :

- Enregistrez et analysez la représentation du nombre sous la forme d’une chaîne de format personnalisé qui reste identique, quelle que soit la culture de l’utilisateur.

- Enregistrez le nombre sous forme de chaîne en utilisant les conventions de mise en forme de la culture dite indifférente, qui est retourné par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Sérialisez le nombre au format binaire et non chaîne.

L’exemple suivant illustre la dernière approche. Il sérialise le tableau de valeurs <xref:System.Double> pour ensuite les désérialiser et les afficher selon les conventions de mise en forme des cultures Français (France) et Anglais (États-Unis).

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

La sérialisation des valeurs de devise est un cas spécial. Sachant qu’une valeur monétaire dépend de l’unité de devise dans laquelle elle est exprimée, il est peu judicieux de la traiter comme une valeur numérique indépendante. En revanche, si vous enregistrez une valeur de devise sous forme de chaîne mise en forme avec un symbole de devise, elle ne peut pas être désérialisée sur un système dont la culture par défaut utilise un autre symbole monétaire, comme le montre l’exemple suivant.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Au lieu de cela, vous devez sérialiser la valeur numérique avec des informations sur la culture, telles que le nom de celle-ci, pour permettre la désérialisation de la valeur et de son symbole de devise indépendamment de la culture active. C’est ce que fait l’exemple suivant en définissant une structure `CurrencyValue` avec deux membres : la valeur <xref:System.Decimal> et le nom de la culture à laquelle appartient la valeur.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Utiliser des paramètres spécifiques à la culture

Dans .NET, la classe <xref:System.Globalization.CultureInfo> représente une culture ou une région particulière. Certaines de ses propriétés retournent des objets qui fournissent des informations spécifiques sur un aspect déterminé d’une culture :

- La propriété <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> retourne un objet <xref:System.Globalization.CompareInfo> qui contient des informations sur la façon dont la culture compare et trie les chaînes.

- La propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> retourne un objet <xref:System.Globalization.DateTimeFormatInfo> qui fournit les informations propres à la culture nécessaires à la mise en forme des données de date et d’heure.

- La propriété <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> retourne un objet <xref:System.Globalization.NumberFormatInfo> qui fournit les informations propres à la culture nécessaires à la mise en forme des données numériques.

- La propriété <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> retourne un objet <xref:System.Globalization.TextInfo> qui fournit des informations sur le système d’écriture de la culture.

En général, ne faites aucune supposition quant aux valeurs des propriétés <xref:System.Globalization.CultureInfo> spécifiques et des objets associés. Vous devez plutôt considérer les données propres à la culture comme des valeurs susceptibles de changer pour les raisons suivantes :

- Les valeurs des propriété individuelles sont susceptibles de changer et d’évoluer dans le temps, à mesure que les données sont corrigées, que des données plus fiables sont disponibles ou que les conventions propres à la culture évoluent.

- Les valeurs des propriétés individuelles peuvent varier entre les différentes versions du .NET ou du système d’exploitation.

- .NET prend en charge les cultures de remplacement. Cela permet de définir une nouvelle culture personnalisée qui complète les cultures standard existants ou qui remplace entièrement une culture standard existante.

- Sur des systèmes Windows, l’utilisateur peut personnaliser les paramètres propres à une culture à l’aide de l’application **Région et langue** du Panneau de configuration. Quand vous instanciez un objet <xref:System.Globalization.CultureInfo>, vous pouvez déterminer s’il reflète ces personnalisations utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>. En règle générale, pour les applications destinées aux utilisateurs finals, veillez à respecter les préférences de mise en forme des utilisateurs de sorte que les données leur soient présentées comme attendu.

## <a name="see-also"></a>Voir aussi

- [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)
- [Bonnes pratiques pour l’utilisation de chaînes](../../../docs/standard/base-types/best-practices-strings.md)
