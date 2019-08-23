---
title: 'Procédure : Analyser une chaîne (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: b97ce93c1018ec48649ab8b259d5f1a07109b9fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956380"
---
# <a name="how-to-parse-a-string-visual-basic"></a>Procédure : Analyser une chaîne (Visual Basic)
Cette rubrique montre comment créer une arborescence XML dans C#.  
  
## <a name="example"></a>Exemple  
 Vous pouvez analyser une chaîne dans Visual Basic à l’aide `XElement.Parse` de la méthode. Toutefois, il est plus efficace d'utiliser des littéraux XML, comme illustré dans le code suivant, car leur impact sur les performances n'est pas aussi sévère que l'analyse de code XML à partir d'une chaîne.  
  
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

- [Analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
