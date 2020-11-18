---
title: 'Procédure : effectuer une transformation XSLT à l’aide d’un assembly'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: 62f3ec511edb7f695580dbfc386773b1dd7b7121
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829477"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="b3456-102">Procédure : effectuer une transformation XSLT à l’aide d’un assembly</span><span class="sxs-lookup"><span data-stu-id="b3456-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="b3456-103">Le compilateur XSLT (xsltc.exe) compile des feuilles de style XSLT et génère un assembly.</span><span class="sxs-lookup"><span data-stu-id="b3456-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="b3456-104">L'assembly peut être passé directement dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3456-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="b3456-105">Pour copier les fichiers XML et XSLT sur votre ordinateur local</span><span class="sxs-lookup"><span data-stu-id="b3456-105">To copy the XML and XSLT files to your local computer</span></span>  
  
- <span data-ttu-id="b3456-106">Copiez le fichier XSLT sur votre ordinateur local et nommez-le Transform.xsl.</span><span class="sxs-lookup"><span data-stu-id="b3456-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
- <span data-ttu-id="b3456-107">Copiez le fichier XML sur votre ordinateur local et nommez-le `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="b3456-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="b3456-108">Pour compiler la feuille de style avec le script activé.</span><span class="sxs-lookup"><span data-stu-id="b3456-108">To compile the style sheet with the script enabled.</span></span>  
  
1. <span data-ttu-id="b3456-109">L'exécution de la commande suivante depuis la ligne de commande crée deux assemblys nommés `Transform.dll` et `Transform_Script1.dll` (C'est le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="b3456-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="b3456-110">Sauf spécification contraire, le nom de la classe et de l'assembly est par défaut celui de la feuille de style principale) :</span><span class="sxs-lookup"><span data-stu-id="b3456-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    <span data-ttu-id="b3456-111">La commande suivante donne explicitement à la classe le nom Transform :</span><span class="sxs-lookup"><span data-stu-id="b3456-111">The following command explicitly sets the class name to Transform:</span></span>  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="b3456-112">Pour inclure l'assembly compilé comme référence lorsque vous compilez votre code.</span><span class="sxs-lookup"><span data-stu-id="b3456-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1. <span data-ttu-id="b3456-113">Vous pouvez inclure un assembly dans Visual Studio en ajoutant une référence dans l'Explorateur de solutions ou à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b3456-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2. <span data-ttu-id="b3456-114">Pour la ligne de commande en C#, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="b3456-114">For the command line with C#, use the following:</span></span>  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. <span data-ttu-id="b3456-115">Pour la ligne de commande en Visual Basic, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="b3456-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="b3456-116">Pour utiliser l'assembly compilé dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b3456-116">To use the compiled assembly in your code.</span></span>  
  
<span data-ttu-id="b3456-117">L'exemple suivant montre comment exécuter la transformation XSLT à l'aide de la feuille de style compilée.</span><span class="sxs-lookup"><span data-stu-id="b3456-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
<span data-ttu-id="b3456-118">Pour établir de manière dynamique une liaison avec l'assembly compilé, remplacez</span><span class="sxs-lookup"><span data-stu-id="b3456-118">To dynamically link to the compiled assembly, replace</span></span>
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
<span data-ttu-id="b3456-119">par</span><span class="sxs-lookup"><span data-stu-id="b3456-119">with</span></span>  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
<span data-ttu-id="b3456-120">dans l'exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b3456-120">in the example above.</span></span> <span data-ttu-id="b3456-121">Pour plus d’informations sur la méthode Assembly. Load, consultez <xref:System.Reflection.Assembly.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3456-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3456-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3456-122">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="b3456-123">XSLT Compiler (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b3456-123">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)
- [<span data-ttu-id="b3456-124">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="b3456-124">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="b3456-125">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="b3456-125">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
