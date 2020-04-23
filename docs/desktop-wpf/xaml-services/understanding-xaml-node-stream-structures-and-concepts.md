---
title: Fonctionnement des concepts et structures du flux de nœud XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: b3de3dca029c5e676fc7cdebc7735cfdade0228a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071618"
---
# <a name="xaml-node-stream-structures-and-concepts"></a>Structures et concepts de flux de nœuds XAML

Les lecteurs de XAML et les auteurs de XAML mis en œuvre dans .NET XAML Services sont basés sur le concept de conception d’un flux de nœuds XAML. Le flux de nœud XAML est une conceptualisation d'un ensemble de nœuds XAML. Dans cette conceptualisation, un processeur XAML parcourt la structure des relations de nœud dans le code XAML une par une. À tout moment, il n'existe qu'un seul enregistrement actuel ou position actuelle dans un flux de nœud XAML ouvert, et de nombreux aspects de l'API ne signalent que les informations disponibles à partir de cette position. Le nœud actuel dans un flux de nœud XAML peut être un objet, un membre ou une valeur. Si les lecteurs XAML traitent le XAML en tant que flux de nœud XAML, ils peuvent communiquer avec les writers XAML et activer un programme qui permet d'afficher, de manipuler ou de modifier le contenu d'un flux de nœud XAML pendant une opération de chemin de chargement ou d'enregistrement impliquant du code XAML. La conception de l’API de lecteur et écrivain de XAML et le concept de flux de nœuds XAML sont semblables aux conceptions et concepts de lecteur et d’auteur apparentés précédents, tels que le modèle d’objet de document de XML (DOM) et le et <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> les classes. Cette rubrique aborde les concepts de flux de nœud XAML et décrit comment écrire des routines qui interagissent avec des représentations XAML au niveau des nœuds XAML.

## <a name="loading-xaml-into-a-xaml-reader"></a>Chargement de XAML dans un lecteur XAML

La classe <xref:System.Xaml.XamlReader> de base ne déclare pas de technique particulière pour le chargement du XAML initial dans un lecteur XAML. En revanche, une classe dérivée déclare et implémente la technique de chargement, y compris les caractéristiques et les contraintes générales de sa source d'entrée pour le XAML. Par exemple, un lecteur <xref:System.Xaml.XamlObjectReader> lit un graphique d'objet à partir de la source d'entrée d'un objet unique, qui représente la racine ou la base. <xref:System.Xaml.XamlObjectReader> génère alors un flux de nœud XAML à partir du graphique d'objet.

La sous-classe définie <xref:System.Xaml.XamlReader> .NET XAML <xref:System.Xaml.XamlXmlReader>Services la plus importante est . La classe<xref:System.Xaml.XamlXmlReader> charge le XAML initial en chargeant un fichier texte directement via un chemin de flux ou de fichier, ou indirectement via une classe du lecteur associé telle que <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> contient l'intégralité de la source d'entrée XAML après son chargement. Toutefois, l'API de base de <xref:System.Xaml.XamlReader> est conçue afin que le lecteur interagisse avec un nœud unique du code XAML. Lors du premier chargement, le premier nœud unique que vous rencontrez est la racine du XAML et son objet de départ.

### <a name="the-xaml-node-stream-concept"></a>Concept du flux de nœud XAML

Si vous êtes plus familier avec un DOM, métaphore d’arbre, ou approche basée sur la requête vers l’accès aux technologies basées sur XML, un moyen utile de conceptualiser un flux de nœuds XAML est le suivant. Imaginez que le XAML chargé est un modèle DOM ou une arborescence dans laquelle tous les nœuds sont développés et présentés de façon linéaire. Dans un modèle DOM, à mesure que vous parcourez les nœuds, vous passez d'un niveau à l'autre, ce qui est pertinent dans ce contexte. Toutefois, le flux de nœud XAML n'effectue pas explicitement de suivi, car il ne gère pas le concept de niveau. Le flux de nœud a une position « actuelle », mais à moins d'avoir vous-même stocké d'autres parties du flux en tant que références, tout aspect du flux de nœud autre que la position du nœud actuel n'est pas visible.

Le concept de flux de nœud XAML présente l'avantage notable que si vous parcourez l'intégralité du flux de nœud, vous êtes assuré d'avoir traité la représentation XAML dans sa totalité. Vous n'avez pas besoin de vérifier si une requête, une opération DOM ou une autre approche non linéaire de traitement des informations a négligé une partie de la représentation XAML complète. Pour cette raison, la représentation sous forme de flux de nœud XAML est idéale pour connecter des lecteurs et writers XAML et pour fournir un système dans lequel vous pouvez insérer votre propre processus entre les phases de lecture et d'écriture d'une opération de traitement XAML. Dans de nombreux cas, l'ordre des nœuds dans le flux de nœud XAML est délibérément optimisé ou réorganisé par les lecteurs XAML, contrairement à l'ordre dans un texte source, un binaire ou un graphique d'objet. Ce comportement permet d'appliquer une architecture de traitement XAML selon laquelle les writers XAML ne sont jamais dans une position qui les oblige à « revenir en arrière » dans le flux de nœud. Idéalement, toutes les opérations d'écriture XAML doivent être en mesure d'agir selon le contexte de schéma ainsi que la position actuelle du flux de nœud.

## <a name="a-basic-reading-node-loop"></a>Boucle de nœud de lecture de base

Une boucle de nœud de lecture de base pour examiner un flux de nœud XAML présente les concepts suivants. Pour les besoins des boucles de nœud décrites dans cette rubrique, supposez que vous lisez un fichier XAML textuel lisible par l'utilisateur à l'aide de <xref:System.Xaml.XamlXmlReader>. Les liens de cette section font référence à l'API de la boucle de nœud XAML implémentée par <xref:System.Xaml.XamlXmlReader>.

- Assurez-vous que vous ne vous trouvez pas à la fin du flux de nœud XAML (vérifiez <xref:System.Xaml.XamlXmlReader.IsEof%2A>, ou utilisez la valeur de retour <xref:System.Xaml.XamlXmlReader.Read%2A> ). Si vous vous trouvez à la fin du flux, il n'y a pas de nœud actuel et vous devez sortir.

- Vérifiez le type de nœud que le flux de nœud XAML expose actuellement en appelant <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Si vous disposez d’un writer d’objet XAML associé directement connecté, vous appelez généralement <xref:System.Xaml.XamlWriter.WriteNode%2A> à ce stade.

- En fonction du <xref:System.Xaml.XamlNodeType> indiqué comme le nœud ou l'enregistrement actuel, appelez l'un des éléments suivants pour obtenir des informations sur le contenu du nœud :

  - Pour une propriété <xref:System.Xaml.XamlXmlReader.NodeType%2A> du nœud <xref:System.Xaml.XamlNodeType.StartMember> ou <xref:System.Xaml.XamlNodeType.EndMember>, appelez <xref:System.Xaml.XamlXmlReader.Member%2A> pour obtenir des informations de <xref:System.Xaml.XamlMember> pour un membre. Le membre peut <xref:System.Xaml.XamlDirective>être un membre, et donc peut-être pas nécessairement un membre conventionnel de type défini de l’objet précédent. Par exemple, `x:Name` appliqué à un objet apparaît comme un membre XAML pour lequel la propriété <xref:System.Xaml.XamlMember.IsDirective%2A> a la valeur true et la propriété <xref:System.Xaml.XamlMember.Name%2A> du membre est `Name`. Les autres propriétés indiquent que cette directive se trouve sous l'espace de noms XAML du langage XAML.

  - Pour une propriété <xref:System.Xaml.XamlXmlReader.NodeType%2A> d'un nœud <xref:System.Xaml.XamlNodeType.StartObject> ou <xref:System.Xaml.XamlNodeType.EndObject>, appelez <xref:System.Xaml.XamlXmlReader.Type%2A> pour obtenir des informations de <xref:System.Xaml.XamlType> pour un objet.

  - Pour une propriété <xref:System.Xaml.XamlXmlReader.NodeType%2A> d'un nœud <xref:System.Xaml.XamlNodeType.Value>, appelez <xref:System.Xaml.XamlXmlReader.Value%2A>. Un nœud est une valeur uniquement s'il est l'expression la plus simple de la valeur d'un membre, ou le texte d'initialisation d'un objet (toutefois, vous devez connaître le comportement de conversion de type, comme indiqué dans une section à venir de cette rubrique).

  - Pour une propriété <xref:System.Xaml.XamlXmlReader.NodeType%2A> d'un nœud <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, appelez <xref:System.Xaml.XamlXmlReader.Namespace%2A> pour obtenir des informations d'espace de noms pour un nœud d'espace de noms.

- Appelez <xref:System.Xaml.XamlXmlReader.Read%2A> pour faire avancer le lecteur XAML au nœud suivant dans le flux de nœud XAML, et recommencez les étapes.

Le flux de nœuds XAML fourni par les lecteurs .NET XAML Services XAML fournit toujours une traversée complète et profonde de tous les nœuds possibles. L'une des techniques de contrôle de flux courantes pour une boucle de nœud XAML est la définition d'un corps dans `while (reader.Read())`et l'activation de <xref:System.Xaml.XamlXmlReader.NodeType%2A> à chaque point de nœud de la boucle de nœud.

Si le flux de nœud se trouve à la fin du fichier, le nœud actuel a la valeur null.

La boucle la plus simple qui utilise un lecteur et un writer ressemble à l'exemple suivant.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Cet exemple de base d'une boucle de nœud XAML de chemin de chargement connecte le lecteur et le writer XAML de façon transparente, comme si vous aviez utilisé <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Mais cette structure de base est ensuite développée pour s'appliquer à votre scénario d'écriture ou de lecture. Voici quelques scénarios possibles :

- Activez <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Effectuez différentes actions en fonction du type de nœud en cours de lecture.

- Dans tous les cas, n'appelez pas <xref:System.Xaml.XamlWriter.WriteNode%2A> . Appelez uniquement <xref:System.Xaml.XamlWriter.WriteNode%2A> dans certains cas de <xref:System.Xaml.XamlXmlReader.NodeType%2A> .

- Dans la logique d'un type de nœud particulier, analysez les caractéristiques de ce nœud et modifiez-les. Par exemple, vous ne pouvez écrire que des objets qui proviennent d’un espace de nom XAML particulier, puis déposer ou reporter tous les objets non de cet espace de nom XAML. Vous pouvez également supprimer ou retraiter différemment toutes les directives XAML que votre système XAML ne prend pas en charge dans le cadre du traitement des membres.

- Définissez un <xref:System.Xaml.XamlObjectWriter> personnalisé qui remplace les méthodes `Write*` , en effectuant éventuellement un mappage de type qui ignore le contexte de schéma XAML.

- Créez le <xref:System.Xaml.XamlXmlReader> pour qu'il utilise un contexte de schéma XAML autre que celui par défaut, de sorte que les différences personnalisées du comportement XAML soient utilisées à la fois par le lecteur et le writer.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Accès au code XAML au-delà du concept de boucle de nœud

Vous pouvez éventuellement utiliser une représentation XAML autrement que sous forme de boucle de nœud XAML. Par exemple, un lecteur XAML peut lire un nœud indexé ou accéder aux nœuds directement par le biais de `x:Name`, `x:Uid`ou d'autres identificateurs. .NET XAML Services ne fournit pas une mise en œuvre complète, mais fournit un modèle suggéré par le biais de services et de types de soutien. Pour plus d’informations, consultez <xref:System.Xaml.IXamlIndexingReader> et <xref:System.Xaml.XamlNodeList>.

## <a name="working-with-the-current-node"></a>Utilisation du nœud actuel

La plupart des scénarios qui utilisent une boucle de nœud XAML ne se limitent pas à la lecture de nœuds. Ils traitent les nœuds actuels et les transfèrent un par un à une implémentation de <xref:System.Xaml.XamlWriter>.

Dans un scénario classique de chemin de chargement, un <xref:System.Xaml.XamlXmlReader> génère un flux de nœud XAML, les nœuds XAML sont traités en fonction de votre logique et du contexte de schéma XAML, puis sont passés à un <xref:System.Xaml.XamlObjectWriter>. Vous intégrez ensuite le graphique d'objet obtenu à votre application ou infrastructure.

Dans un scénario classique de chemin d'enregistrement, un <xref:System.Xaml.XamlObjectReader> lit le graphique d'objet, les nœuds XAML sont traités individuellement et un <xref:System.Xaml.XamlXmlWriter> exporte le résultat sérialisé en tant que fichier texte XAML. La clé est que les chemins et les scénarios impliquent de travailler avec exactement un nœud XAML à la fois, et les nœuds XAML sont disponibles pour le traitement d’une manière standardisée qui est définie par le système de type XAML et the.NET API XAML Services.

### <a name="frames-and-scope"></a>Frames et portée

Une boucle de nœud XAML parcourt un flux de nœud XAML de façon linéaire. Le flux de nœud parcourt des objets, des membres contenant d'autres objets, et ainsi de suite. Il est souvent utile d'effectuer le suivi de la portée au sein du flux de nœud XAML en implémentant un concept de frame et pile. Cela est particulièrement vrai si vous ajustez activement le flux de nœud pendant son traitement. La prise en charge de frame et de pile que vous implémentez dans le cadre de votre logique de boucle de nœud peut dénombrer les portées `StartObject` (ou `GetObject`) et `EndObject` à mesure que vous descendez dans une structure de nœud XAML, d'un point de vue DOM.

## <a name="traversing-and-entering-object-nodes"></a>Parcourir des nœuds d'objet et y entrer

Le premier nœud d'un flux de nœud ouvert par un lecteur XAML est le nœud d'objet de début de l'objet racine. Par définition, cet objet est toujours un nœud d'objet unique, sans homologue. Dans tous les exemples de code XAML réel, l'objet racine est défini pour avoir une ou plusieurs propriétés contenant d'autres objets, et ces propriétés contiennent des nœuds membres. Les nœuds membres contiennent à leur tour un ou plusieurs nœuds d'objet, ou peuvent aussi se terminer dans un nœud de valeur. L'objet racine définit généralement les portées de nom XAML, lesquelles sont syntaxiquement assignées en tant qu'attributs dans le balisage de texte XAML, mais mappent vers un type de nœud `Namescope` dans la représentation de flux de nœud XAML.

Prenons l’exemple XAML suivant (c’est L’exemple arbitraire de XAML, non soutenu par les types existants en .NET). Supposons que dans ce modèle objet, `FavorCollection` est un `List<T>` de `Favor`, `Balloon` et `NoiseMaker` peuvent être assignés à `Favor`, la propriété `Balloon.Color` est associée à un objet `Color` semblable à la façon dont WPF définit les couleurs en tant que noms de couleurs connus, et `Color` prend en charge un convertisseur de type pour la syntaxe d'attribut.

|Balisage XAML|Flux de nœud XAML résultant|
|-----------------|--------------------------------|
|`<Party`|`Namespace` pour `Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject` pour `Party`|
|`<Party.Favors>`|`StartMember` pour `Party.Favors`|
||Nœud`StartObject` pour la collection `FavorCollection`implicite|
||Nœud`StartMember` pour la propriété des éléments de la collection `FavorCollection` implicite.|
|`<Balloon`|`StartObject` pour `Balloon`|
|`Color="Red"`|`StartMember` pour `Color`<br /><br /> `Value` pour la chaîne de valeur d'attribut `"Red"`<br /><br /> `EndMember` pour `Color`|
|`HasHelium="True"`|`StartMember` pour `HasHelium`<br /><br /> `Value` pour la chaîne de valeur d'attribut `"True"`<br /><br /> `EndMember` pour `HasHelium`|
|`>`|`EndObject` pour `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` pour `NoiseMaker`<br /><br /> `StartMember` pour `_Initialization`<br /><br /> `Value` pour la chaîne de valeur d'initialisation `"Loudest"`<br /><br /> `EndMember` pour `_Initialization`<br /><br /> `EndObject` pour `NoiseMaker`|
||Nœud`EndMember` pour la propriété des éléments de la collection `FavorCollection` implicite.|
||Nœud`EndObject` pour la collection `FavorCollection`implicite|
|`</Party.Favors>`|`EndMember` pour `Favors`|
|`</Party>`|`EndObject` pour `Party`|

Dans le flux de nœud XAML, vous pouvez compter sur le comportement suivant :

- Si un nœud `Namespace` existe, il est ajouté au flux immédiatement avant le `StartObject` qui a déclaré l'espace de noms XAML avec `xmlns`. Réexaminez le tableau précédent avec l'exemple de flux de nœud XAML. Notez la façon dont les nœuds `StartObject` et `Namespace` semblent être transposés par rapport à leur position de déclaration dans le balisage de texte. Ceci est représentatif du comportement selon lequel les nœuds d'espace de noms apparaissent toujours avant le nœud auquel ils s'appliquent dans le flux de nœud. Cette conception s'explique par le fait que les informations d'espace de noms sont essentielles pour les writers d'objet et doivent être connues avant que le writer d'objet ne tente d'effectuer le mappage de type ou de traiter l'objet. Il est plus simple de placer les informations d'espace de noms XAML avant sa portée d'application dans le flux, plutôt que de traiter toujours le flux de nœud dans l'ordre présenté.

- Par conséquent, vous lisez d'abord un ou plusieurs nœuds `Namespace` dans la plupart des cas de balisage réels lors du parcours des nœuds à partir du début, plutôt que le `StartObject` de la racine.

- Un nœud `StartObject` peut être suivi de `StartMember`, `Value`ou d'un `EndObject`immédiat. Il n'est jamais immédiatement suivi d'un autre `StartObject`.

- Un nœud `StartMember` peut être suivi d'un nœud `StartObject`, `Value`ou d'un nœud `EndMember`immédiat. Il peut être suivi d'un nœud `GetObject`, pour les membres dont la valeur est censée provenir d'une valeur existante de l'objet parent et non d'un nœud `StartObject` qui instancierait une nouvelle valeur. Il peut également être suivi d'un nœud `Namespace` , qui s'applique à un nœud `StartObject`à venir. Il n'est jamais immédiatement suivi d'un autre `StartMember`.

- Un nœud `Value` représente la valeur elle-même. Il n'y a pas de « EndValue ». Il peut être suivi uniquement d'un nœud `EndMember`.

  - Le texte d'initialisation XAML de l'objet, tel qu'il peut être utilisé par la construction, n'entraîne pas de structure objet-valeur. À la place, un nœud membre dédié à un membre nommé `_Initialization` est créé. Ce nœud membre contient la chaîne de valeur d'initialisation. S'il existe, le membre `_Initialization` est toujours le premier nœud `StartMember`. Le membre`_Initialization` peut être qualifié dans certaines représentations des services XAML avec la portée de nom XAML du langage XAML, pour préciser que le membre `_Initialization` n'est pas une propriété définie dans les types de stockage.

  - Une combinaison membre-valeur représente un paramètre d'attribut de la valeur. Un convertisseur de valeurs peut éventuellement être impliqué dans le traitement de cette valeur, et la valeur est une chaîne simple. Toutefois, cela n'est pas évalué tant qu'un writer d'objet XAML traite ce flux de nœud. Le writer d'objet XAML possède le contexte de schéma XAML, le mappage de système de type et d'autres prises en charge nécessaires pour la conversion de valeurs.

- Un nœud `EndMember` peut être suivi d'un nœud `StartMember` pour un membre suivant ou d'un nœud `EndObject` pour le propriétaire du membre.

- Un nœud `EndObject` peut être suivi d'un nœud `EndMember` . Il peut également être suivi d'un nœud `StartObject` si les objets sont des homologues dans les éléments d'une collection. Il peut également être suivi d'un nœud `Namespace` , qui s'applique à un nœud `StartObject`à venir.

  - Dans le seul cas de la fermeture du flux de nœud entier, le nœud `EndObject` de la racine n'est pas suivi, le lecteur se trouve à la fin du fichier et <xref:System.Xaml.XamlReader.Read%2A> renvoie `false`.

## <a name="value-converters-and-the-xaml-node-stream"></a>Convertisseurs de valeurs et flux de nœud XAML

Un convertisseur de valeurs est un terme général qui désigne une extension de balisage, un convertisseur de type (y compris les sérialiseurs de valeur) ou une autre classe dédiée signalée comme convertisseur de valeurs via le système de type XAML. Dans le flux de nœud XAML, l'utilisation d'un convertisseur de type et celle d'une extension de balisage ont des représentations très différentes.

### <a name="type-converters-in-the-xaml-node-stream"></a>Convertisseurs de type et flux de nœud XAML

Un attribut défini, qui finit par entraîner une utilisation de convertisseur de type, est signalé dans le flux de nœud XAML comme une valeur de membre. Le flux de nœud XAML ne tente pas de générer un objet d'instance de convertisseur de type et de lui passer la valeur. L'implémentation de la conversion d'un convertisseur de type requiert l'appel du contexte de schéma XAML et son utilisation pour le mappage de type. De la même façon, le contexte de schéma XAML est requis indirectement pour déterminer la classe de convertisseur de type qui doit être utilisée pour traiter la valeur. Quand vous utilisez le contexte de schéma XAML par défaut, ces informations sont disponibles à partir du système de type XAML. Si vous avez besoin des informations de classe de convertisseur de type au niveau du flux de nœud XAML avant la connexion à un writer XAML, vous pouvez les obtenir à partir des informations de <xref:System.Xaml.XamlMember> du membre défini. Mais autrement, l’entrée de convertisseur de type doit être préservée dans le flux de nœuds XAML comme valeur simple jusqu’à ce que le reste des opérations qui nécessitent le système de cartographie de type et le contexte du schéma XAML sont exécutés, par exemple la création d’objet par un auteur d’objets XAML.

Par exemple, considérez la structure de définition de classe suivante et son utilisation de code XAML :

```csharp
public class BoardSizeConverter : TypeConverter {
  //converts from string to an int[2] by splitting on an "x" char
}
public class GameBoard {
  [TypeConverter(typeof(BoardSizeConverter))]
  public int[] BoardSize; //2x2 array, initialization not shown
}
```

```xaml
<GameBoard BoardSize="8x8"/>
```

Une représentation textuelle du flux de nœud XAML pour cette utilisation peut être exprimée comme suit :

`StartObject` avec <xref:System.Xaml.XamlType> représentant `GameBoard`

`StartMember` avec <xref:System.Xaml.XamlMember> représentant `BoardSize`

Le nœud`Value` , avec la chaîne de texte «`8x8`»

`EndMember` correspond à `BoardSize`

`EndObject` correspond à `GameBoard`

Notez qu'il n'y a aucune instance de convertisseur de type dans ce flux de nœud. Mais vous pouvez obtenir des informations sur le convertisseur de type en appelant <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> sur le <xref:System.Xaml.XamlMember> pour `BoardSize`. Si vous disposez d'un contexte de schéma XAML valide, vous pouvez également appeler les méthodes du convertisseur en obtenant une instance à partir de <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensions de balisage dans le flux de nœud XAML

L'utilisation d'une extension de balisage est signalée dans le flux de nœud XAML en tant que nœud d'objet dans un membre, où l'objet représente une instance d'extension de balisage. Par conséquent, une extension de balisage est présentée plus explicitement dans la représentation de flux de nœud qu'une utilisation de convertisseur de type, et comporte plus d'informations. Les informations relatives à<xref:System.Xaml.XamlMember> ne vous renseignent pas sur l'extension de balisage, car l'utilisation est situationnelle et varie selon chaque cas de balisage possible. Elle n'est ni dédiée ni implicite pour un type ou un membre, contrairement aux convertisseurs de type.

C'est le cas notamment de la représentation de flux de nœud des extensions de balisage en tant que nœuds d'objet, même si l'utilisation de l'extension de balisage a été effectuée sous forme d'attribut dans le balisage de texte XAML (ce qui se produit souvent). Les cas d'utilisation d'extension de balisage qui utilisaient un formulaire d'élément objet explicite sont traités de la même façon.

Un nœud d'objet d'extension de balisage peut comporter des membres de cette extension de balisage. La représentation de flux de nœud XAML conserve l'utilisation de cette extension de balisage, qu'il s'agisse d'une utilisation de paramètres positionnels ou d'une utilisation avec des paramètres nommés explicites.

Pour une utilisation de paramètres positionnels, le flux de nœud XAML contient une propriété `_PositionalParameters` définie en langage XAML qui enregistre cette utilisation. Cette propriété est un <xref:System.Collections.Generic.List%601> générique avec une contrainte <xref:System.Object> . La contrainte est un objet et non une chaîne, car en théorie l'utilisation d'un paramètre positionnel peut contenir des utilisations d'extension de balisage imbriquées. Pour accéder aux paramètres positionnels à partir de l'utilisation, vous pouvez effectuer une itération dans la liste et utiliser les indexeurs pour les valeurs de liste individuelles.

Pour l'utilisation d'un paramètre nommé, chaque paramètre nommé est représenté comme un nœud du membre du même nom dans le flux de nœud. Les valeurs de membre ne sont pas nécessairement des chaînes, car il peut y avoir une utilisation d'extension de balisage imbriquée.

`ProvideValue` n'est pas encore appelé dans l'extension de balisage. Toutefois, il est appelé si vous connectez un lecteur et un writer XAML de sorte que `WriteEndObject` soit appelé sur le nœud d'extension de balisage quand vous l'examinez dans le flux de nœud. Pour cette raison, vous avez généralement besoin du même contexte de schéma XAML que celui que vous utilisez pour former le graphique d'objet sur le chemin de chargement. Sinon, `ProvideValue` dans n'importe quelle extension de balisage peut lever des exceptions, car les services attendus ne sont pas disponibles.

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Membres définis en langage XAML et XML dans le flux de nœud XAML

Certains membres sont présentés dans un flux de nœud XAML en raison des interprétations et des conventions d'un lecteur XAML, et non par le biais de la recherche ou la construction d'un <xref:System.Xaml.XamlMember> explicite. Souvent, ces membres sont des directives XAML. Dans certains cas, c'est la lecture du code XAML qui présente la directive dans le flux de nœud XAML. En d’autres termes, le texte d’entrée originale XAML n’a pas précisé explicitement la directive membre, mais le lecteur XAML insère la directive afin de satisfaire une convention structurelle XAML et de rapporter des informations dans le flux de nœuds XAML avant que ces informations ne sont perdues.

La liste suivante note tous les cas où un lecteur XAML est censé introduire une directive XAML nœud membre, et comment ce nœud membre est identifié dans .NET XAML Services mises en œuvre.

- **Texte d'initialisation d'un nœud d'objet :** le nom de ce nœud membre est `_Initialization`, il représente une directive XAML et est défini dans l'espace de noms XAML du langage XAML. Vous pouvez en obtenir une entité statique à partir de <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Paramètres positionnels d'une extension de balisage :** le nom de ce nœud membre est `_PositionalParameters`et est défini dans l'espace de noms XAML du langage XAML. Il contient toujours une liste générique d'objets, chacun d'eux étant un paramètre positionnel préalablement séparé par fractionnement à partir du caractère délimiteur `,` fourni dans le XAML d'entrée. Vous pouvez obtenir une entité statique pour la directive de paramètres positionnels à partir de <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Contenu inconnu :** le nom de ce nœud membre est `_UnknownContent`. Proprement dit, il s'agit d'une directive <xref:System.Xaml.XamlDirective>définie dans l'espace de noms XAML du langage XAML. Cette directive est utilisée comme sentinelle au cas où  un élément objet XAML contient le contenu de la source XAML, mais qu'aucune propriété de contenu ne peut être déterminée dans le contexte de schéma XAML actuellement disponible. Vous pouvez détecter ce cas dans un flux de nœud XAML en recherchant les membres nommés `_UnknownContent`. Si aucune autre action n'est effectuée dans un flux de nœud XAML de chemin de chargement, le nœud <xref:System.Xaml.XamlObjectWriter> par défaut lève une exception sur une tentative de `WriteEndObject` quand il rencontre le membre `_UnknownContent` sur un objet. Le writer <xref:System.Xaml.XamlXmlWriter> par défaut ne lève pas d'exception et traite le membre comme s'il était implicite. Vous pouvez obtenir une entité statique pour `_UnknownContent` à partir de <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Propriété de collecte d’une collection :** Bien que le type DE CLR de soutien d’une classe de collecte qui est utilisé pour XAML a généralement une propriété dédiée nommée qui détient les éléments de collecte, cette propriété n’est pas connue d’un système de type XAML avant la résolution de type de support. Au lieu de cela, le flux de nœud XAML présente un espace réservé `Items` en tant que membre du type XAML de la collection. Dans la mise en œuvre de .NET XAML Services, le nom de cette directive ou membre dans le flux de nœuds est `_Items`. Une constante pour cette directive peut être obtenue à partir de <xref:System.Xaml.XamlLanguage.Items%2A>.

    Notez qu’un flux de nœuds XAML peut contenir une propriété Items avec des éléments qui s’avèrent ne pas être parsables en fonction de la résolution de type de support et le contexte du schéma XAML. Par exemple,

- **Membres définis par XML :** Le `xml:base`XML-défini `xml:lang` `xml:space` , et les membres sont `base` `lang`signalés `space` comme directives XAML nommé , , et dans .NET XAML Services implémentations. L'espace de noms pour ces directives est l'espace de noms XML `http://www.w3.org/XML/1998/namespace`. Des constantes pour chacune d'elles peuvent être obtenues à partir de <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Ordre des nœuds

Dans certains cas, <xref:System.Xaml.XamlXmlReader> modifie l'ordre des nœuds XAML dans le flux de nœud XAML, par rapport à l'ordre des nœuds affichés dans le balisage ou traités en tant que XML. Cela permet de classer les nœuds de sorte qu'un <xref:System.Xaml.XamlObjectWriter> puisse traiter le flux de nœud uniquement vers l'avant.  Dans .NET XAML Services, le lecteur XAML réorganise les nœuds plutôt que de laisser cette tâche à l’auteur XAML, comme une optimisation des performances pour les consommateurs XAML écrivain objet du flux de nœuds.

Certaines directives sont conçues spécifiquement pour fournir plus d'informations sur la création d'un objet à partir d'un élément objet. Ces directives sont les suivantes : `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. .NET XAML Services lecteurs XAML tentent de placer ces directives comme les `StartObject`premiers membres dans le flux de nœuds suivant un objet , pour des raisons qui sont expliquées dans la section suivante.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Comportement de XamlObjectWriter et ordre des nœuds

Un nœud`StartObject` pour un <xref:System.Xaml.XamlObjectWriter> ne signifie pas nécessairement que le writer d'objet XAML doit immédiatement créer l'instance d'objet. XAML comprend plusieurs caractéristiques linguistiques qui permettent d’initialiser un objet avec une entrée supplémentaire, et de ne pas compter entièrement sur l’invocation d’un constructeur sans paramètres pour produire l’objet initial, et seulement alors la mise en place des propriétés. Ces fonctionnalités sont notamment les suivantes : <xref:System.Windows.Markup.XamlDeferLoadAttribute>; texte d'initialisation ; [x: TypeArguments](xtypearguments-directive.md); paramètres positionnels d'une extension de balisage ; méthodes de fabrique et nœuds [x: Arguments](xarguments-directive.md) associés (XAML 2009). Chacun de ces cas retarde la construction réelle de l’objet, et parce que le flux de nœud est réorganisé, l’auteur d’objets XAML peut s’appuyer sur un comportement de construire réellement l’instance chaque fois qu’un membre de démarrage est rencontré qui n’est pas spécifiquement une directive de construction pour ce type d’objet.

### <a name="getobject"></a>GetObject

`GetObject` représente un nœud XAML dans lequel un writer d'objet XAML doit obtenir la valeur de la propriété contenant l'objet au lieu de construire un objet. Généralement, un nœud `GetObject` est rencontré dans un flux de nœud XAML pour un objet collection ou un objet dictionnaire, quand la propriété conteneur est délibérément en lecture seule dans le modèle d'objet du type de stockage. Dans ce cas, la collection ou le dictionnaire est souvent créé et initialisé (généralement vide) par la logique d'initialisation d'un type propriétaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xaml.XamlObjectReader>
- [Services XAML](index.md)
- [Espaces de noms XAML](namespaces.md)
