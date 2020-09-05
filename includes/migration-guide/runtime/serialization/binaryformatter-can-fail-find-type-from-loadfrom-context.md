---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497846"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter peut ne pas parvenir à trouver le type dans le contexte LoadFrom

#### <a name="details"></a>Détails

Depuis .NET Framework 4.5, un certain nombre de modifications de <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> peuvent entraîner des différences de désérialisation quand vous utilisez <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> pour désérialiser des types qui avaient été chargés dans le contexte LoadFrom. Ces modifications sont dues aux nouvelles façons dont <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> charge maintenant un type qui provoque un comportement différent quand un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> tente plus tard une désérialisation en ce type. Le binder de sérialisation par défaut n’effectue pas automatiquement des recherches dans le contexte LoadFrom, bien qu’il ait pu fonctionner dans certains cas en fonction de l’ancien comportement de XmlSerializer. En raison des modifications, quand un type est chargé à partir d’un assembly chargé dans un contexte différent, une <xref:System.IO.FileNotFoundException?displayProperty=fullName> peut être levée.

#### <a name="suggestion"></a>Suggestion

Si cette exception se produit, la propriété <code>Binder</code> de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> peut être définie sur un binder personnalisé qui va rechercher le type approprié.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>Puis le binder personnalisé :<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
