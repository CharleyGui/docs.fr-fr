---
title: LINQ à la vue d’ensemble XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: b4b40acaaf3787e67e4d6efb1efb1ecd4f117427
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586326"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ à la vue d’ensemble XML (Visual Basic)
Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes. Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est une approche à jour et repensée de la programmation avec XML. Elle propose les fonctionnalités de modification des documents en mémoire du modèle DOM (Document Objet Model) et prend en charge les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.  
  
## <a name="linq-to-xml-developers"></a>Développeurs LINQ to XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cible un large éventail de développeurs. Pour un développeur qui souhaite simplement se faciliter la tâche, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rend le XML plus abordable en fournissant une expérience de requête semblable à SQL. Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.  
  
 Les développeurs professionnels peuvent utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour accroître considérablement leur productivité. Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant. Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.  
  
## <a name="what-is-linq-to-xml"></a>Qu'est-ce que LINQ to XML ?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est une prenant en charge LINQ en mémoire XML interface de programmation qui vous permet de travailler avec XML à partir de .NET Framework langages de programmation.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s’apparente au modèle DOM en ce sens qu’il place le document XML en mémoire. Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet. Cependant, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] diffère du modèle DOM : Il fournit un nouveau modèle d’objet qui est plus léger et plus facile à manipuler, et qui tire parti des fonctionnalités de langage dans Visual Basic.  
  
 Le principal avantage de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est son intégration avec [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs. La capacité de requête de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est comparable en terme de fonctionnalités (mais pas en termes de syntaxe) à XQuery et XPath. L’intégration de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] en Visual Basic fournit un typage, compilation au moment la vérification et une meilleure prise en charge du débogueur.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présente également l'avantage de pouvoir utiliser des résultats de requête en tant que paramètres de constructeurs d'objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>, ce qui constitue une approche puissante pour la création d'arborescences XML. Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.  
  
 Par exemple, vous pouvez avoir un bon de commande XML standard comme décrit dans [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md). En utilisant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pourriez exécuter la requête suivante afin d'obtenir la valeur d'attribut de numéro de référence pour chaque élément de la commande fournisseur :  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence. Pour obtenir ces informations, vous pourriez exécuter la requête suivante :  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Outre ces fonctionnalités [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une interface de programmation XML améliorée. Grâce à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez :  
  
- charger du code XML à partir de fichiers ou de flux ;  
  
- sérialiser du code XML vers des fichiers ou des flux ;  
  
- créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;  
  
- interroger du code XML à l'aide d'axes de type XPath ;  
  
- manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;  
  
- valider des arborescences XML à l'aide de XSD ;  
  
- utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.  
  
## <a name="creating-xml-trees"></a>Création d'arborescences XML  
 L'un des principaux avantages liés à la programmation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tient à la facilité de création d'arborescences XML. Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 Le compilateur Visual Basic convertit des littéraux XML en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] les appels de méthode.  
  
 Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq>
- [Bien démarrer (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [Vue d’ensemble de LINQ to XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
