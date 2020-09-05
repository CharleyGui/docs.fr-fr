---
ms.openlocfilehash: e56d896f093d6cd28ed0d6640ba154e5d4593c6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496286"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a><span data-ttu-id="7f8ca-101">L’extension d’entité DTD de XmlTextReader est limitée à 10 000 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f8ca-101">XmlTextReader DTD entity expansion is limited to 10,000,000 characters</span></span>

#### <a name="details"></a><span data-ttu-id="7f8ca-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7f8ca-102">Details</span></span>

<span data-ttu-id="7f8ca-103">L’extension d’entité DTD est désormais limitée à 10 000 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f8ca-103">DTD entity expansion is now limited to 10,000,000 characters.</span></span> <span data-ttu-id="7f8ca-104">Le chargement des fichiers XML sans extension d'entité DTD ou avec une extension d'entité DTD limitée reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="7f8ca-104">Loading XML files without DTD entity expansion or with limited DTD entity expansion is unaffected.</span></span> <span data-ttu-id="7f8ca-105">Les fichiers avec des entités DTD qui s'étendent à plus de 10 000 000 caractères ne se chargent pas et lèvent désormais une exception.</span><span class="sxs-lookup"><span data-stu-id="7f8ca-105">Files with DTD entities that expand to more than 10,000,000 characters fail to load, and now throw an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f8ca-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7f8ca-106">Suggestion</span></span>

<span data-ttu-id="7f8ca-107">Si la limite de l’extension d’entité DTD n’est pas suffisante, la valeur peut être remplacée par la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities>.</span><span class="sxs-lookup"><span data-stu-id="7f8ca-107">If the limit of DTD entity expansion is too low 10,000,000, the value can be overridden with the <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> property.</span></span> <span data-ttu-id="7f8ca-108">Un <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> avec la valeur <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> correcte peut être passé à <code>XmlReader.Create</code> qui prend <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (c’est-à-dire <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span><span class="sxs-lookup"><span data-stu-id="7f8ca-108">An <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> with the proper <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> value can be passed to <code>XmlReader.Create</code> that takes <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (ie. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span></span>

| <span data-ttu-id="7f8ca-109">Name</span><span class="sxs-lookup"><span data-stu-id="7f8ca-109">Name</span></span>    | <span data-ttu-id="7f8ca-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="7f8ca-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f8ca-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="7f8ca-111">Scope</span></span>   |<span data-ttu-id="7f8ca-112">Edge</span><span class="sxs-lookup"><span data-stu-id="7f8ca-112">Edge</span></span>|
|<span data-ttu-id="7f8ca-113">Version</span><span class="sxs-lookup"><span data-stu-id="7f8ca-113">Version</span></span>|<span data-ttu-id="7f8ca-114">4,5</span><span class="sxs-lookup"><span data-stu-id="7f8ca-114">4.5</span></span>|
|<span data-ttu-id="7f8ca-115">Type</span><span class="sxs-lookup"><span data-stu-id="7f8ca-115">Type</span></span>|<span data-ttu-id="7f8ca-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="7f8ca-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7f8ca-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="7f8ca-117">Affected APIs</span></span>

- <xref:System.Xml.XmlTextReader?displayProperty=nameWithType>
- <xref:System.Xml.XmlTextReader.%23ctor>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)>

<!--

#### Affected APIs

- `T:System.Xml.XmlTextReader`
- `M:System.Xml.XmlTextReader.#ctor`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.Xml.XmlNameTable)`

-->
