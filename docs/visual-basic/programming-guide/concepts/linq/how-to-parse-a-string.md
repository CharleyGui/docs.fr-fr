---
title: 'Procédure : analyser une chaîne'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 0a9076fc516bb8e6bc74732ca252fabfeda43d53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398010"
---
# <a name="how-to-parse-a-string-visual-basic"></a>Comment : analyser une chaîne (Visual Basic)
Cette rubrique montre comment créer une arborescence XML en C#.  
  
## <a name="example"></a>Exemple  
 Vous pouvez analyser une chaîne dans Visual Basic à l’aide de la `XElement.Parse` méthode. Toutefois, il est plus efficace d'utiliser des littéraux XML, comme illustré dans le code suivant, car leur impact sur les performances n'est pas aussi sévère que l'analyse de code XML à partir d'une chaîne.  
  
 En utilisant des littéraux XML, vous pouvez simplement copier et coller votre code XML dans votre programme Visual Basic.  
  
> [!NOTE]
> L'analyse de texte ou le chargement d'un document XML à partir d'un fichier texte est moins efficace que la construction fonctionnelle. Si vous initialisez une arborescence XML à partir de code, la construction fonctionnelle requiert moins de temps processeur que l’analyse de texte.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Analyse XML (Visual Basic)](parsing-xml.md)
