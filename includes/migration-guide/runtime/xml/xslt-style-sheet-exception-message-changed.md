---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620524"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="794de-101">Le message de l’exception relative aux feuilles de style XSLT a été changé</span><span class="sxs-lookup"><span data-stu-id="794de-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="794de-102">Détails</span><span class="sxs-lookup"><span data-stu-id="794de-102">Details</span></span>

<span data-ttu-id="794de-103">Dans le .NET Framework 4,5, le texte du message d’erreur lorsqu’un fichier XSLT est trop complexe est &quot; la feuille de style est trop complexe. &quot; Dans les versions précédentes, le message d’erreur était &quot; erreur de compilation XSLT. &quot; Le code d’application qui dépend du texte du message d’erreur ne fonctionnera plus.</span><span class="sxs-lookup"><span data-stu-id="794de-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="794de-104">Toutefois, comme les types d’exception restent les mêmes, cette modification ne devrait pas avoir d’impact réel.</span><span class="sxs-lookup"><span data-stu-id="794de-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="794de-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="794de-105">Suggestion</span></span>

<span data-ttu-id="794de-106">Mettez à jour le code d’application qui dépend du message d’exception de cette condition d’erreur pour qu’il attende le nouveau message ou (encore mieux) mettez à jour le code pour qu’il dépende uniquement du type d’exception (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), qui n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="794de-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="794de-107">Nom</span><span class="sxs-lookup"><span data-stu-id="794de-107">Name</span></span>    | <span data-ttu-id="794de-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="794de-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="794de-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="794de-109">Scope</span></span>   |<span data-ttu-id="794de-110">Edge</span><span class="sxs-lookup"><span data-stu-id="794de-110">Edge</span></span>|
|<span data-ttu-id="794de-111">Version</span><span class="sxs-lookup"><span data-stu-id="794de-111">Version</span></span>|<span data-ttu-id="794de-112">4,5</span><span class="sxs-lookup"><span data-stu-id="794de-112">4.5</span></span>|
|<span data-ttu-id="794de-113">Type</span><span class="sxs-lookup"><span data-stu-id="794de-113">Type</span></span>|<span data-ttu-id="794de-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="794de-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="794de-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="794de-115">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|
