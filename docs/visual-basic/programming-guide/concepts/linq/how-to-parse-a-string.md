---
title: 'Comment : analyser une chaîne'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 31bae00eb3ebf0d8e64fc657693e8c0767c4f5d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344496"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="509f1-102">Comment : analyser une chaîne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="509f1-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="509f1-103">Cette rubrique montre comment créer une arborescence XML dans C#.</span><span class="sxs-lookup"><span data-stu-id="509f1-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="509f1-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="509f1-104">Example</span></span>  
 <span data-ttu-id="509f1-105">Vous pouvez analyser une chaîne dans Visual Basic à l’aide de la méthode `XElement.Parse`.</span><span class="sxs-lookup"><span data-stu-id="509f1-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="509f1-106">Toutefois, il est plus efficace d'utiliser des littéraux XML, comme illustré dans le code suivant, car leur impact sur les performances n'est pas aussi sévère que l'analyse de code XML à partir d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="509f1-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="509f1-107">En utilisant des littéraux XML, vous pouvez simplement copier et coller votre code XML dans votre programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="509f1-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="509f1-108">L'analyse de texte ou le chargement d'un document XML à partir d'un fichier texte est moins efficace que la construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="509f1-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="509f1-109">Si vous initialisez une arborescence XML à partir de code, la construction fonctionnelle requiert moins de temps processeur que l’analyse de texte.</span><span class="sxs-lookup"><span data-stu-id="509f1-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="509f1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="509f1-110">See also</span></span>

- [<span data-ttu-id="509f1-111">Analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="509f1-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
