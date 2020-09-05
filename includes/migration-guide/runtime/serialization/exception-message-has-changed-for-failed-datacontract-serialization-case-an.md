---
ms.openlocfilehash: 8d0404c728231f596500653d556e3be6fcc20c2c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496148"
---
### <a name="exception-message-has-changed-for-failed-datacontract-serialization-in-case-of-an-unknown-type"></a><span data-ttu-id="89774-101">Le message d’exception a été modifié pour l’échec de la sérialisation de DataContract dans le cas d’un type inconnu</span><span class="sxs-lookup"><span data-stu-id="89774-101">Exception message has changed for failed DataContract serialization in case of an unknown type</span></span>

#### <a name="details"></a><span data-ttu-id="89774-102">Détails</span><span class="sxs-lookup"><span data-stu-id="89774-102">Details</span></span>

<span data-ttu-id="89774-103">À compter de .NET Framework 4.6, le message d’exception affiché si un <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> ou <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> ne parvient pas à sérialiser ni à désérialiser en l’absence de « types connus » a été clarifié.</span><span class="sxs-lookup"><span data-stu-id="89774-103">Beginning in the .NET Framework 4.6, the exception message given if a <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> or <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> fails to serialize or deserialize due to missing 'known types' has been clarified.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="89774-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="89774-104">Suggestion</span></span>

<span data-ttu-id="89774-105">Les applications ne doivent pas dépendre de messages d’exceptions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="89774-105">Apps should not depend on specific exception messages.</span></span> <span data-ttu-id="89774-106">Si une application dépend de ce message, mettez-la à jour pour qu’elle attende le nouveau message ou (de préférence) modifiez-la pour qu’elle dépende uniquement du type d’exception.</span><span class="sxs-lookup"><span data-stu-id="89774-106">If an app depends on this message, either update it to expect the new message or (preferably) change it to depend only on the exception type.</span></span>

| <span data-ttu-id="89774-107">Name</span><span class="sxs-lookup"><span data-stu-id="89774-107">Name</span></span>    | <span data-ttu-id="89774-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="89774-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="89774-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="89774-109">Scope</span></span>   |<span data-ttu-id="89774-110">Edge</span><span class="sxs-lookup"><span data-stu-id="89774-110">Edge</span></span>|
|<span data-ttu-id="89774-111">Version</span><span class="sxs-lookup"><span data-stu-id="89774-111">Version</span></span>|<span data-ttu-id="89774-112">4,6</span><span class="sxs-lookup"><span data-stu-id="89774-112">4.6</span></span>|
|<span data-ttu-id="89774-113">Type</span><span class="sxs-lookup"><span data-stu-id="89774-113">Type</span></span>|<span data-ttu-id="89774-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="89774-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="89774-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="89774-115">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Runtime.Serialization.Json.DataContractJsonSerializerSettings)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Runtime.Serialization.DataContractSerializerSettings)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Runtime.Serialization.Json.DataContractJsonSerializerSettings)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Runtime.Serialization.DataContractSerializerSettings)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`

-->
