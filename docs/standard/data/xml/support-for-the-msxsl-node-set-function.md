---
title: Prise en charge de la fonction msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 5022b298cb20796edbc54e951d8b06043697d832
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155592"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="bdd11-102">Prise en charge de la fonction msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="bdd11-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="bdd11-103">La fonction `msxsl:node-set` vous permet de convertir un fragment d’arborescence résultat en une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="bdd11-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="bdd11-104">La collection de nœuds obtenue contient toujours un seul nœud et représente le nœud racine de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="bdd11-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdd11-105">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="bdd11-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="bdd11-106">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="bdd11-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="bdd11-107">Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="bdd11-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="bdd11-108">La fonction `msxsl:node-set` vous permet de convertir un fragment d’arborescence résultat en une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="bdd11-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="bdd11-109">La collection de nœuds obtenue contient toujours un seul nœud et représente le nœud racine de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="bdd11-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd11-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bdd11-110">Example</span></span>  
 <span data-ttu-id="bdd11-111">Dans l'exemple suivant, `$var` est une variable qui est une arborescence de nœuds dans la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="bdd11-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="bdd11-112">L'instruction for-each associée à la fonction `node-set` permet à l'utilisateur d'itérer sur cette arborescence de nœuds comme une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="bdd11-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="bdd11-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="bdd11-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="bdd11-114">Sortie</span><span class="sxs-lookup"><span data-stu-id="bdd11-114">Output</span></span>  
 <span data-ttu-id="bdd11-115">La sortie de la transformation est :</span><span class="sxs-lookup"><span data-stu-id="bdd11-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdd11-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd11-116">See also</span></span>

- [<span data-ttu-id="bdd11-117">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="bdd11-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
