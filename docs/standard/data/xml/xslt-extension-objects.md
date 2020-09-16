---
title: Objets d'extension XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: ff50cbb561f9da5ea0877ded1de6fd3d5c424a7e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555957"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="f9974-102">Objets d'extension XSLT</span><span class="sxs-lookup"><span data-stu-id="f9974-102">XSLT Extension Objects</span></span>
<span data-ttu-id="f9974-103">Les objets d’extension permettent d’étendre les fonctionnalités des feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="f9974-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="f9974-104">Ils sont gérés par la classe <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="f9974-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="f9974-105">L’utilisation d’un objet d’extension plutôt que d’un script intégré présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="f9974-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="f9974-106">Offre une meilleure encapsulation et réutilisation des classes.</span><span class="sxs-lookup"><span data-stu-id="f9974-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="f9974-107">Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="f9974-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="f9974-108">Des objets d’extension XSLT sont ajoutés à l’objet <xref:System.Xml.Xsl.XsltArgumentList> à l’aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9974-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="f9974-109">Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.</span><span class="sxs-lookup"><span data-stu-id="f9974-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9974-110">Le jeu d'autorisations FullTrust est requis pour appeler la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9974-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="f9974-111">Pour plus d’informations, consultez les pages [Sécurité d’accès du code](../../../framework/misc/code-access-security.md) et [Jeux d’autorisations nommés](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f9974-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="f9974-112">Les types de données retournés par les objets d’extension correspondent à l’un des quatre types de données de base XPath : `number`, `string`, `Boolean` et `node set`.</span><span class="sxs-lookup"><span data-stu-id="f9974-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="f9974-113">Les méthodes définies avec le mot clé `params`, qui permet de transmettre un nombre non spécifié de paramètres, ne sont actuellement pas prises en charge par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f9974-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f9974-114">Les feuilles de style XSLT qui utilisent une méthode définie avec le mot clé `params` ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="f9974-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="f9974-115">Pour plus d’informations, consultez la page [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="f9974-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="f9974-116">Pour utiliser un objet d’extension XSLT</span><span class="sxs-lookup"><span data-stu-id="f9974-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="f9974-117">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l'objet d'extension à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9974-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="f9974-118">Appelez l’objet d’extension à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="f9974-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="f9974-119">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9974-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9974-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9974-120">See also</span></span>

- [<span data-ttu-id="f9974-121">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="f9974-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="f9974-122">XSLT et la sécurité</span><span class="sxs-lookup"><span data-stu-id="f9974-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
