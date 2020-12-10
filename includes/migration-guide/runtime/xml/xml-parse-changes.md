---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009049"
---
### <a name="xml-parsing-changes"></a><span data-ttu-id="90168-101">Modifications de l’analyse XML</span><span class="sxs-lookup"><span data-stu-id="90168-101">XML parsing changes</span></span>

| <span data-ttu-id="90168-102">Name</span><span class="sxs-lookup"><span data-stu-id="90168-102">Name</span></span>    | <span data-ttu-id="90168-103">Valeur</span><span class="sxs-lookup"><span data-stu-id="90168-103">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="90168-104">Étendue</span><span class="sxs-lookup"><span data-stu-id="90168-104">Scope</span></span>   | <span data-ttu-id="90168-105">Secondaire</span><span class="sxs-lookup"><span data-stu-id="90168-105">Minor</span></span>   |
| <span data-ttu-id="90168-106">Version</span><span class="sxs-lookup"><span data-stu-id="90168-106">Version</span></span> | <span data-ttu-id="90168-107">4.5.2</span><span class="sxs-lookup"><span data-stu-id="90168-107">4.5.2</span></span>   |
| <span data-ttu-id="90168-108">Type</span><span class="sxs-lookup"><span data-stu-id="90168-108">Type</span></span>    | <span data-ttu-id="90168-109">Runtime</span><span class="sxs-lookup"><span data-stu-id="90168-109">Runtime</span></span> |

#### <a name="details"></a><span data-ttu-id="90168-110">Détails</span><span class="sxs-lookup"><span data-stu-id="90168-110">Details</span></span>

<span data-ttu-id="90168-111">Pour des raisons de sécurité, les modifications suivantes ont été introduites dans les API d’analyse XML :</span><span class="sxs-lookup"><span data-stu-id="90168-111">For security reasons, the following changes were introduced into XML parsing APIS:</span></span>

- <span data-ttu-id="90168-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> a la valeur 10 millions lorsque <xref:System.Xml.XmlReaderSettings> est initialisé.</span><span class="sxs-lookup"><span data-stu-id="90168-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> is set to 10 million when <xref:System.Xml.XmlReaderSettings> is initialized.</span></span>
- <span data-ttu-id="90168-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> a la valeur `null` par défaut.</span><span class="sxs-lookup"><span data-stu-id="90168-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> is set to `null` by default.</span></span>

> [!NOTE]
> <span data-ttu-id="90168-114"><xref:System.Xml.XmlReaderSettings> est utilisé par tous les analyseurs XML. ainsi, bien que cette modification aide le <xref:System.Xml.XmlReader> cas, elle affecte également d’autres scénarios.</span><span class="sxs-lookup"><span data-stu-id="90168-114"><xref:System.Xml.XmlReaderSettings> is used by all XML parsers, so while this change helps the <xref:System.Xml.XmlReader> case, it also affects other scenarios.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90168-115">Suggestion</span><span class="sxs-lookup"><span data-stu-id="90168-115">Suggestion</span></span>

<span data-ttu-id="90168-116">Pour rétablir le comportement précédent, vous pouvez définir une valeur dans le registre.</span><span class="sxs-lookup"><span data-stu-id="90168-116">To revert to the previous behavior, you can set a value in the registry.</span></span> <span data-ttu-id="90168-117">Ajoutez une valeur DWORD nommée `EnableLegacyXmlSettings` à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` clé de Registre et affectez-lui la valeur `1` .</span><span class="sxs-lookup"><span data-stu-id="90168-117">Add a DWORD value named `EnableLegacyXmlSettings` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` registry key, and set its value to `1`.</span></span> <span data-ttu-id="90168-118">Vous pouvez également ajouter la valeur de Registre dans la ruche HKEY_CURRENT_USER à la place.</span><span class="sxs-lookup"><span data-stu-id="90168-118">You can also add the registry value in the HKEY_CURRENT_USER hive instead.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90168-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="90168-119">Affected APIs</span></span>

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

<span data-ttu-id="90168-120">En outre, toute API XML qui dépend de <xref:System.Xml.XmlResolver> , directement ou indirectement, est affectée.</span><span class="sxs-lookup"><span data-stu-id="90168-120">In addition, any XML API that depends on <xref:System.Xml.XmlResolver>, either directly or indirectly, is affected.</span></span>

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
