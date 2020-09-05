---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497846"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a><span data-ttu-id="3eafa-101">BinaryFormatter peut ne pas parvenir à trouver le type dans le contexte LoadFrom</span><span class="sxs-lookup"><span data-stu-id="3eafa-101">BinaryFormatter can fail to find type from LoadFrom context</span></span>

#### <a name="details"></a><span data-ttu-id="3eafa-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3eafa-102">Details</span></span>

<span data-ttu-id="3eafa-103">Depuis .NET Framework 4.5, un certain nombre de modifications de <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> peuvent entraîner des différences de désérialisation quand vous utilisez <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> pour désérialiser des types qui avaient été chargés dans le contexte LoadFrom.</span><span class="sxs-lookup"><span data-stu-id="3eafa-103">As of .NET Framework 4.5, a number of <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> changes may cause differences in deserialization when using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> to deserialize types that had been loaded in the LoadFrom context.</span></span> <span data-ttu-id="3eafa-104">Ces modifications sont dues aux nouvelles façons dont <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> charge maintenant un type qui provoque un comportement différent quand un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> tente plus tard une désérialisation en ce type.</span><span class="sxs-lookup"><span data-stu-id="3eafa-104">These changes are due to the new ways <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> now loads a type which causes different behavior when a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> attempts to deserialize to that type later on.</span></span> <span data-ttu-id="3eafa-105">Le binder de sérialisation par défaut n’effectue pas automatiquement des recherches dans le contexte LoadFrom, bien qu’il ait pu fonctionner dans certains cas en fonction de l’ancien comportement de XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="3eafa-105">The default serialization binder does not automatically search the LoadFrom context, although it may have worked in some circumstances based on the old behavior of XmlSerializer.</span></span> <span data-ttu-id="3eafa-106">En raison des modifications, quand un type est chargé à partir d’un assembly chargé dans un contexte différent, une <xref:System.IO.FileNotFoundException?displayProperty=fullName> peut être levée.</span><span class="sxs-lookup"><span data-stu-id="3eafa-106">Due to the changes, when a type is being loaded from an assembly loaded in a different context, a <xref:System.IO.FileNotFoundException?displayProperty=fullName> may be thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3eafa-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3eafa-107">Suggestion</span></span>

<span data-ttu-id="3eafa-108">Si cette exception se produit, la propriété <code>Binder</code> de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> peut être définie sur un binder personnalisé qui va rechercher le type approprié.</span><span class="sxs-lookup"><span data-stu-id="3eafa-108">If this exception is seen, the <code>Binder</code> property of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> can be set to a custom binder that will find the correct type.</span></span><pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre><span data-ttu-id="3eafa-109">Puis le binder personnalisé :</span><span class="sxs-lookup"><span data-stu-id="3eafa-109">And then the custom binder:</span></span><pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="3eafa-110">Name</span><span class="sxs-lookup"><span data-stu-id="3eafa-110">Name</span></span>    | <span data-ttu-id="3eafa-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="3eafa-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3eafa-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="3eafa-112">Scope</span></span>   |<span data-ttu-id="3eafa-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3eafa-113">Edge</span></span>|
|<span data-ttu-id="3eafa-114">Version</span><span class="sxs-lookup"><span data-stu-id="3eafa-114">Version</span></span>|<span data-ttu-id="3eafa-115">4,5</span><span class="sxs-lookup"><span data-stu-id="3eafa-115">4.5</span></span>|
|<span data-ttu-id="3eafa-116">Type</span><span class="sxs-lookup"><span data-stu-id="3eafa-116">Type</span></span>|<span data-ttu-id="3eafa-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="3eafa-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3eafa-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="3eafa-118">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
