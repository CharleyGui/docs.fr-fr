---
title: Mappage entre JSON et XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 9049e622803396126890d4c88b9fee2a100f17c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747743"
---
# <a name="mapping-between-json-and-xml"></a>Mappage entre JSON et XML
Les lecteurs et writers produits par le <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> fournissent une API XML sur le contenu de JavaScript Objet Notation (JSON). JSON encode des données à l'aide d'un sous-ensemble de littéraux d'objet JavaScript. Les lecteurs et writers produits par cette fabrique sont également utilisés lorsque le contenu JSON est envoyé ou reçu par les applications Windows Communication Foundation (WCF) à l’aide de la <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ou le <xref:System.ServiceModel.WebHttpBinding>.

En cas d'initialisation avec le contenu JSON, le lecteur JSON se comporte de la même façon qu'un lecteur XML textuel sur une instance de XML. Le writer JSON, lorsqu'il reçoit une séquence d'appels qui sur un lecteur XML textuel produit une certaine instance XML, écrit un contenu JSON. Le mappage entre cette instance de XML et le contenu JSON est décrit dans cette rubrique pour une utilisation dans des scénarios avancés.

En interne, JSON est représenté comme un infoset XML lors du traitement par WCF. Normalement vous n’êtes pas obligé de se préoccuper de cette représentation interne, car le mappage n’est seulement une logique : JSON est normalement pas physiquement converti au format XML en mémoire ou converti au format JSON à partir de XML. Le mappage signifie que les API XML sont utilisées pour accéder au contenu JSON.

Lorsque WCF utilise JSON, le scénario habituel est que le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est branché automatiquement par le <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> comportement, ou par le <xref:System.ServiceModel.Description.WebHttpBehavior> comportement lorsque cela est approprié. Le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> comprend le mappage entre JSON et les jeux d'informations XML et fonctionne comme s'il traite directement avec JSON. (Il est possible d'utiliser le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> avec tout lecteur ou writer XML à condition que le XML se conforme au mappage suivant).

Dans les scénarios avancés, il peut devenir nécessaire d'accéder directement au mappage suivant. Ces scénarios se produisent lorsque vous souhaitez sérialiser et désérialiser JSON de manières personnalisées, sans avoir à compter sur le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ou lors d'un traitement direct avec le type <xref:System.ServiceModel.Channels.Message> pour les messages qui contiennent JSON. Le mappage JSON-XML est également utilisé pour l'enregistrement des messages. Lorsque vous utilisez la fonctionnalité de journalisation des messages dans WCF, les messages JSON sont enregistrés au format XML selon le mappage décrit dans la section suivante.

Pour clarifier le concept d'un mappage, l'exemple suivant est celui d'un document JSON.

```json
{"product":"pencil","price":12}
```

Pour lire ce document JSON à l'aide de l'un des lecteurs évoqués précédemment, utilisez la même séquence d'appels <xref:System.Xml.XmlDictionaryReader> que pour lire le document XML suivant.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

En outre, si le message JSON dans l’exemple est reçu par WCF et connecté, vous voyez le fragment XML dans le journal précédent.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mappage entre JSON et le jeu d'informations XML
Formellement, le mappage se fait entre JSON comme décrit dans [RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) (sauf avec certaines restrictions assouplies et autres restrictions ajoutées) et le code XML infoset (et pas XML textuel) comme décrit dans [informations XML Définir](https://go.microsoft.com/fwlink/?LinkId=98809). Consultez cette rubrique pour les définitions des *éléments d’information* et champs entre [crochets].

Un document JSON vierge est mappé à un document XML vide, et un document XML vierge est mappé à un document JSON vierge. Sur le mappage XML à JSON, qui précède un espace blanc et d’espace blanc de fin après le document ne sont pas autorisés.

Le mappage est défini entre un élément DII (Document Information Item) ou un élément EII (Element Information Item) et JSON. L'élément EII, ou la propriété de l'élément DII [élément de document] est appelé l'élément JSON racine. Notez que les fragments de document (XML avec plusieurs éléments racine) ne sont pas pris en charge dans ce mappage.

Exemple : le document suivant :

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

Et les éléments suivants :

```xml
<root type="number">42</root>
```

Ces deux éléments ont un mappage à JSON. Le <`root`> élément est l’élément JSON racine dans les deux cas.

De plus, les éléments suivants doivent être pris en compte dans le cas d'un élément DII :

- Certains éléments dans la liste [enfants] ne doivent pas être présents. Ne comptez pas sur ce fait pour la lecture du XML mappé à partir de JSON.

- La liste [enfants] ne contient aucun élément d'informations de commentaire.

- La liste [enfants] ne contient aucun élément d'informations DTD.

- La liste [enfants] ne contient aucun élément d’informations personnelles des informations (PI) (le `<?xml…>` déclaration n’est pas considéré comme un élément d’informations PI)

- Le jeu [notations] est vide.

- Le jeu [entités non analysées] est vide.

Exemple : Le document suivant n’a aucun mappage à JSON parce que [enfants] contient un PI et un commentaire.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

L'EII pour l'élément JSON racine a les caractéristiques suivantes :

- [nom local] a la valeur "racine".

- [nom d'espace de noms] n'a aucune valeur.

- [préfixe] n'a aucune valeur.

- [enfants] peut contenir des éléments EII (qui représentent des éléments internes décrits plus loin) ou des éléments CII (éléments d'informations de caractère décrits plus loin) ou aucun d'entre eux, mais pas les deux.

- [attributs] peut contenir les éléments AII (Attribute Information Items) facultatifs suivants

- L'attribut de type JSON ("type") décrit plus loin. Cet attribut est utilisé pour conserver le type JSON (chaîne, nombre, booléen, objet, tableau ou null) dans le XML mappé.

- L’attribut de nom de contrat de données («\_\_type ») comme décrit plus loin. Cet attribut peut être présent uniquement si l'attribut de type JSON est aussi présent et sa [valeur normalisée] est "objet." Cet attribut est utilisé par le `DataContractJsonSerializer` pour conserver des informations de type de contrat de données - par exemple, dans les cas polymorphes où un type dérivé est sérialisé et où un type de base est attendu. Si vous n'utilisez le `DataContractJsonSerializer`, dans la plupart des cas, cet attribut est ignoré.

- [espaces de noms dans l’étendue] contient la liaison de « xml » à `http://www.w3.org/XML/1998/namespace` comme mandaté par la spécification infoset.

- [enfants], [attributs] et [espaces de noms dans l'étendue] ne doivent pas avoir d'éléments autres que ceux spécifiés précédemment et [attributs d'espace de noms] ne doit pas avoir de membres, mais ne compte pas sur ces faits pour la lecture du XML mappé à partir de JSON.

Exemple : Le document suivant n’a aucun mappage à JSON parce que [attributs d’espace de noms] n’est pas vide.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

L'élément AII pour l'attribut de type JSON a les caractéristiques suivantes :

- [nom d'espace de noms] n'a aucune valeur.
- [préfixe] n'a aucune valeur.
- [nom local] est "type".
- [valeur normalisée] est une des valeurs de type possibles décrite dans la section suivante.
- [spécifié] a la valeur `true`.
- [type d'attribut] n'a aucune valeur.
- [références] n'a aucune valeur.

L'élément AII pour l'attribut de nom de contrat de données a les caractéristiques suivantes :

- [nom d'espace de noms] n'a aucune valeur.
- [préfixe] n'a aucune valeur.
- [nom local] est «\_\_type » (deux traits de soulignement et ensuite « type »).
- [valeur normalisée] est toute chaîne Unicode valide. Le mappage de cette chaîne à JSON est décrit dans la section suivante.
- [spécifié] a la valeur `true`.
- [type d'attribut] n'a aucune valeur.
- [références] n'a aucune valeur.

Les éléments internes contenus dans l'élément JSON racine ou d'autres éléments internes ont les caractéristiques suivantes :

- [nom local] peut avoir n’importe quelle valeur décrit plus loin.
- [nom d'espace de noms], [préfixe], [enfants], [attributs], [attributs d'espace de noms], et [espaces de noms dans l'étendue] sont soumis aux mêmes règles que l'élément JSON racine.

Dans l'élément JSON racine et les éléments internes, l'attribut de type JSON définit le mappage à JSON et les [enfants] possibles et leur interprétation. [Valeur normalisée] de l’attribut respecte la casse et doit être en minuscule et ne peut pas contenir d’espace blanc.

|[valeur normalisée] de l’élément AII de l’attribut de Type JSON|[enfants] autorisés de l'élément EII correspondant|Mappage à JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (ou absence de l'élément AII de type JSON)<br /><br /> Un `string` et l'absence de l'élément AII de type JSON sont les mêmes que la valeur par défaut `string`.<br /><br /> Ainsi, `<root> string1</root>` mappe à "string1" `string` JSON.|0 ou plusieurs éléments CII|JSON `string` (JSON RFC, section 2.5). Chaque `char` est un caractère qui correspond au [code de caractère] du CII. En l'absence d'élément CII, il mappe à un `string` JSON vide.<br /><br /> Exemple : L’élément suivant mappe à un fragment JSON :<br /><br /> `<root type="string">42</root>`<br /><br /> Le fragment JSON est "42".<br /><br /> Sur le mappage XML à JSON, les caractères qui doivent faire l'objet d'une séquence d'échappement sont mappés aux caractères d'échappement, tous les autres sont mappés aux caractères de non échappement. Le caractère « / » est spécial : il est ignoré même s’il n’a pas à être (écrit comme «\\/ »).<br /><br /> Exemple : L’élément suivant mappe à un fragment JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Le fragment JSON est « le \\» da\\/ta\\» ».<br /><br /> Sur le mappage JSON à XML, les caractères échappés et les caractères non échappés ne sont pas correctement mappés au [code de caractère] correspondant.<br /><br /> Exemple : Le fragment JSON « \u0041BC » mappe à l’élément XML suivant.<br /><br /> `<root type="string">ABC</root>`<br /><br /> La chaîne peut être entourée par un espace blanc ('ws' dans la section 2 de la RFC JSON) qui ne sont pas mappé au XML.<br /><br /> Exemple : Le JSON fragmente « ABC », (il existe des espaces avant le premier guillemet double), mappe à l’élément XML suivant.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Tout espace blanc dans XML mappe à un espace blanc dans JSON.<br /><br /> Exemple : L’élément XML suivant mappe à un fragment JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Le fragment JSON est " A BC ".|
|`number`|1 ou plusieurs éléments CII|JSON `number` (JSON RFC, section 2.4), peut-être entouré par un espace blanc. Chaque caractère dans la combinaison nombre/espace est un caractère qui correspond au [code de caractère] du CII.<br /><br /> Exemple : L’élément suivant mappe à un fragment JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Le fragment JSON est    42.<br /><br /> (L’espace blanc est conservé).|
|`boolean`|4 ou 5 éléments CII (qui correspond à `true` ou `false`), peuvent être entourés par des éléments CII de blancs supplémentaires.|Une séquence CII qui correspond à la chaîne "true" est mappée au littéral `true`, et une séquence CII qui correspond à la chaîne "false" est mappée au littéral `false`. Entourant l’espace blanc est conservé.<br /><br /> Exemple : L’élément suivant mappe à un fragment JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Le fragment JSON is `false`.|
|`null`|Aucun autorisé.|Littéral `null`. Sur le mappage JSON à XML, le `null` peut être entouré par un espace blanc ('ws' dans section 2) qui ne sont pas mappé au XML.<br /><br /> Exemple : L’élément suivant mappe à un fragment JSON.<br /><br /> `<root type="null"/>`<br /><br /> ou Gestionnaire de configuration<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Le fragment JSON dans les deux cas est `Null`.|
|`object`|0 ou plusieurs éléments EII.|Un `begin-object` (accolade ouvrante) comme dans la section 2.2 de la FRC JSON, suivi d'un enregistrement membre pour chaque élément EII décrit plus loin. En présence de plusieurs éléments EII, il y a des séparateurs de valeur (virgules) entre les enregistrements membre. Cet ensemble est suivi par un objet de fin (accolade fermante).<br /><br /> Exemple : L’élément suivant mappe au fragment JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Le fragment JSON is `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Si l'attribut de type de contrat de données est présent sur le mappage XML à JSON, tout membre supplémentaire est inséré au début. Son nom est le [nom local] de l’attribut de Type de contrat de données («\_\_type »), et sa valeur est l’attribut [valeur normalisée]. Inversement, sur le mappage JSON à XML, si le premier nom de l’enregistrement-membre est le [nom local] de l’attribut de Type de contrat de données (autrement dit, «\_\_type »), un attribut de Type de contrat de données correspondante est présent dans le XML mappé, mais un élément EII correspondant n’est pas présent. Notez que cet enregistrement membre doit se produire en premier dans l'objet JSON pour que ce mappage spécial s'applique. Il s'agit d'une nouveauté par rapport au traitement JSON habituel dans lequel l'ordre des enregistrements membres n'est pas significatif.<br /><br /> Exemple :<br /><br /> Le fragment JSON suivant mappe au XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Le XML est le code suivant.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Notez que le \_ \_élément AII de type est présent, mais il existe aucune \_ \_type élément EII.<br /><br /> Toutefois, si l'ordre dans le JSON est inversé comme indiqué dans l'exemple suivant.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Le XML correspondant est indiqué.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Autrement dit, \__type cesse d’avoir une signification spéciale et mappe à un élément EII comme d’habitude, pas un élément AII.<br /><br /> Les règles d'échappement ou de non échappement pour l'élément AII [valeur normalisée] en cas de mappage à une valeur JSON sont les mêmes que pour les chaînes JSON spécifiées dans la ligne "chaîne" de ce tableau.<br /><br /> Exemple :<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> à l'exemple précédent peut être mappé au JSON suivant.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Sur un mappage XML à JSON, le premier élément EII [nom local] ne doit pas être «\_\_type ».<br /><br /> Espace blanc (`ws`) n’est jamais généré sur XML pour le mappage JSON pour les objets et est ignoré sur JSON à mappage XML.<br /><br /> Exemple : Le fragment JSON suivant mappe à un élément XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> L'élément XML est indiqué dans le code suivant.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 ou plusieurs éléments EII|Un tableau ouvrant (crochet ouvrant) comme dans la section 2.3 de la RFC JSON suivi d'un enregistrement de tableau pour chaque élément EII comme cela est décrit plus loin. En présence de plusieurs éléments EII, il y a des séparateurs de valeur (virgules) entre les enregistrements de tableau. L'ensemble est suivi d'un tableau fermant.<br /><br /> Exemple : L’élément XML suivant mappe à un fragment JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Le fragment JSON est `["aaa","bbb"]`<br /><br /> Espace blanc (`ws`) n’est jamais généré sur XML pour le mappage JSON pour les tableaux et est ignoré sur JSON à mappage XML.<br /><br /> Exemple : Un fragment JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> L'élément XML auquel il mappe.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Les enregistrements membres fonctionnent comme suit :

- Le [nom local] de l'élément interne mappe à la partie `string` du `member` défini dans la section 2.2 de la RFC JSON.

Exemple : L’élément suivant mappe à un fragment JSON.

```xml
<root type="object"/>
<myLocalName type="string">aaa</myLocalName>
</root >
```

Le fragment JSON suivant est affiché.

```json
{"myLocalName":"aaa"}
```

- Sur le mappage XML à JSON, les caractères qui doivent faire l'objet d'une séquence d'échappement dans JSON le sont, et tous les autres ne le sont pas. Le caractère "/", même s'il ne s'agit pas d'un caractère qui doit faire l'objet d'une séquence d'échappement, est néanmoins échappé (ce qui n'est pas nécessaire sur le mappage JSON à XML). Cela est requis pour prendre en charge le format ASP.NET AJAX pour les données `DateTime` dans JSON.

- Sur le mappage JSON au XML, tous les caractères (y compris les caractères non échappés, si nécessaire) sont acceptés pour former un `string` qui produit un [nom local].

- Les éléments internes [enfants] mappent à la valeur dans section 2.2, selon `JSON Type Attribute` comme pour `Root JSON Element`. Plusieurs niveaux d'imbrication des éléments EII (y compris l'imbrication dans des tableaux) sont autorisés.

Exemple : L’élément suivant mappe à un fragment JSON.

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

Le fragment JSON suivant est celui auquel il est mappé.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> Il n'y a aucune étape d'encodage XML dans le mappage précédent. Par conséquent, WCF prend uniquement en charge les documents JSON où tous les caractères dans les noms de clé sont les caractères valides dans les noms d’élément XML. Par exemple, le document JSON {« < » : « a »} n’est pas pris en charge, car < n’est pas un nom valide pour un élément XML.

La situation inverse (caractères valide dans XML mais pas dans JSON) ne provoque pas de problèmes étant donné que le mappage précédent inclut des étapes d'échappement et de non échappement JSON.

Les enregistrements du tableau fonctionnent comme suit :

- Le [nom local] de l'élément interne est "élément."

- [enfants] de l'élément interne mappe à la valeur dans la section 2.3, selon l'attribut de type JSON comme pour l'élément JSON racine. Plusieurs niveaux d'imbrication des éléments EII (y compris l'imbrication dans des objets) sont autorisés.

Exemple : L’élément suivant mappe à un fragment JSON.

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

Les éléments suivants sont le fragment JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Sérialisation JSON autonome](stand-alone-json-serialization.md)
