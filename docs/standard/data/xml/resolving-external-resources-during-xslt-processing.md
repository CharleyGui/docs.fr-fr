---
title: Résolution de ressources externes lors du traitement XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: d38aea1a54c93b00ec14c6aac7ed11ceba288f7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291498"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="2af46-102">Résolution de ressources externes lors du traitement XSLT</span><span class="sxs-lookup"><span data-stu-id="2af46-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="2af46-103">Lors d'une transformation XSLT, il peut s'avérer nécessaire de résoudre des ressources externes à plusieurs moments.</span><span class="sxs-lookup"><span data-stu-id="2af46-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="2af46-104">Utilisation de la classe XmlResolver</span><span class="sxs-lookup"><span data-stu-id="2af46-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="2af46-105">La classe <xref:System.Xml.XmlResolver> permet de résoudre des ressources externes.</span><span class="sxs-lookup"><span data-stu-id="2af46-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="2af46-106">Le tableau suivant décrit l'implication de l'objet <xref:System.Xml.XmlResolver> dans le traitement XSLT.</span><span class="sxs-lookup"><span data-stu-id="2af46-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="2af46-107">Tâche XSLT</span><span class="sxs-lookup"><span data-stu-id="2af46-107">XSLT task</span></span>|<span data-ttu-id="2af46-108">Utilité de XmlResolver</span><span class="sxs-lookup"><span data-stu-id="2af46-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="2af46-109">Compilation de la feuille de style</span><span class="sxs-lookup"><span data-stu-id="2af46-109">Compile the style sheet.</span></span>|<span data-ttu-id="2af46-110">Résolution de l'URI de la feuille de style</span><span class="sxs-lookup"><span data-stu-id="2af46-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="2af46-111">-et-</span><span class="sxs-lookup"><span data-stu-id="2af46-111">-and-</span></span><br /><br /> <span data-ttu-id="2af46-112">Résolution des références URI dans tout élément `xsl:import` ou `xsl:include`</span><span class="sxs-lookup"><span data-stu-id="2af46-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="2af46-113">Exécution de la feuille de style</span><span class="sxs-lookup"><span data-stu-id="2af46-113">Execute the style sheet.</span></span>|<span data-ttu-id="2af46-114">Résolution de l'URI dans le document de contexte</span><span class="sxs-lookup"><span data-stu-id="2af46-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="2af46-115">-et-</span><span class="sxs-lookup"><span data-stu-id="2af46-115">-and-</span></span><br /><br /> <span data-ttu-id="2af46-116">Résolution des références URI dans toute fonction XSLT `document()`</span><span class="sxs-lookup"><span data-stu-id="2af46-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="2af46-117">Les méthodes <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> et <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> comprennent des surcharges qui prennent un objet <xref:System.Xml.XmlResolver> comme l'un de leurs arguments.</span><span class="sxs-lookup"><span data-stu-id="2af46-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="2af46-118">Si aucun <xref:System.Xml.XmlResolver> n'est spécifié, un <xref:System.Xml.XmlUrlResolver> par défaut sans informations d'identification est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2af46-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="2af46-119">La liste suivante décrit les cas dans lesquels vous pouvez préférer spécifier un objet <xref:System.Xml.XmlResolver> :</span><span class="sxs-lookup"><span data-stu-id="2af46-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="2af46-120">Si le traitement XSLT doit accéder à une ressource réseau qui nécessite une authentification, vous pouvez utiliser un objet <xref:System.Xml.XmlResolver> avec les informations d'identification nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2af46-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="2af46-121">Si vous souhaitez limiter les ressources auxquelles le traitement XSLT peut accéder, vous pouvez utiliser un objet <xref:System.Xml.XmlSecureResolver> avec toutes les autorisations correctes.</span><span class="sxs-lookup"><span data-stu-id="2af46-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="2af46-122">La classe <xref:System.Xml.XmlSecureResolver> doit être utilisée si vous devez ouvrir une ressource non contrôlée ou non fiable.</span><span class="sxs-lookup"><span data-stu-id="2af46-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="2af46-123">Pour personnaliser le comportement, vous pouvez implémenter votre propre classe <xref:System.Xml.XmlResolver> et l'utiliser pour résoudre les ressources.</span><span class="sxs-lookup"><span data-stu-id="2af46-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="2af46-124">Pour vous assurer qu’aucune ressource externe n’est accessible, vous pouvez spécifier `null` pour l’argument <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="2af46-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2af46-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2af46-125">Example</span></span>  
 <span data-ttu-id="2af46-126">L'exemple suivant compile une feuille de style stockée sur une ressource réseau.</span><span class="sxs-lookup"><span data-stu-id="2af46-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="2af46-127">Un objet <xref:System.Xml.XmlUrlResolver> spécifie les informations d'identification nécessaires pour accéder à la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="2af46-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="2af46-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2af46-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="2af46-129">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="2af46-129">XSLT Transformations</span></span>](xslt-transformations.md)
