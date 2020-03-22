---
title: Vue d’ensemble de LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266896"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Vue d'ensemble de LINQ to XML dans Visual Basic
Visual Basic fournit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] un support pour les littérales XML et les propriétés d’axe XML. Cela vous permet d’utiliser une syntaxe familière et pratique pour travailler avec XML dans votre code de base visuel. *Les littérals XML* vous permettent d’inclure XML directement dans votre code. *Les propriétés de l’axe XML* vous permettent d’accéder aux nœuds pour enfants, aux nœuds descendants et aux attributs d’un littératique XML. Pour plus d’informations, voir [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) et [Accéder à XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]est une API de programmation XML en mémoire conçue spécifiquement pour tirer parti de la requête intégrée au langage (LINQ). Bien que vous puissiez appeler directement les API LINQ, seul Visual Basic vous permet de déclarer les littérals XML et d’accéder directement aux propriétés de l’axe XML.  
  
> [!NOTE]
> Les littérales XML et les propriétés d’axe XML ne sont pas prises en charge dans le code déclaratif dans une page ASP.NET. Pour utiliser les fonctionnalités Visual Basic XML, placez votre code dans une page de code derrière votre application ASP.NET.  
  
 [Bouton de lecture](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Pour les démonstrations vidéo connexes, voir [Comment puis-je démarrer avec LINQ à XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) et [Comment puis-je créer des feuilles de calcul Excel en utilisant LINQ à XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).
  
## <a name="creating-xml"></a>Création de code XML  
 Il existe deux façons de créer des arbres XML dans Visual Basic. Vous pouvez déclarer un XML littéral directement dans le code, ou vous pouvez utiliser les API LINQ pour créer l’arbre. Les deux processus permettent au code de refléter la structure finale de l’arbre XML. Par exemple, l’exemple de code suivant crée un élément XML :  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Pour plus d’informations, voir [Créer XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Accès et navigation XML  
 Visual Basic fournit des propriétés d’axe XML pour accéder et naviguer dans les structures XML. Ces propriétés vous permettent d’accéder aux éléments et aux attributs XML en spécifiant les noms des éléments pour enfants XML. Vous pouvez également appeler explicitement les méthodes LINQ pour naviguer et localiser les éléments et les attributs. Par exemple, l’exemple de code suivant utilise les propriétés de l’axe XML pour désigner les attributs et les éléments pour enfants d’un élément XML. L’exemple de code utilise une requête LINQ pour récupérer les éléments de l’enfant et les produire sous forme d’éléments XML, effectuant efficacement une transformation.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Pour plus d’informations, voir [Accéder à XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Visual Basic vous permet de spécifier un alias `Imports` à un espace de nom XML global en utilisant la déclaration. L’exemple suivant montre `Imports` comment utiliser l’instruction pour importer un espace de nom XML :  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Vous pouvez utiliser un alias XML namespace lorsque vous accédez aux propriétés de l’axe XML et déclarez les littérals XML pour les documents et les éléments XML.  
  
 Vous pouvez <xref:System.Xml.Linq.XNamespace> récupérer un objet pour un préfixe d’espace de nom particulier en utilisant l’opérateur [GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Pour plus d’informations, voir [Déclaration des importations (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Utilisation de XML Namespaces dans XML Literals  
 L’exemple suivant montre <xref:System.Xml.Linq.XElement> comment créer un objet `ns`qui utilise l’espace de nom global :  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Le compilateur Visual Basic traduit les littérals XML qui contiennent des alias XML namespace en code `xmlns` équivalent qui utilise la notation XML pour l’utilisation des espaces de nom XML, avec l’attribut. Lorsqu’il est compilé, le code dans l’exemple de la section précédente produit essentiellement le même code exécutable que l’exemple suivant :  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Utilisation de XML Namespaces dans XML Axis Properties  
 Les espaces de nom XML déclarés dans les littérals XML ne sont pas disponibles pour une utilisation dans les propriétés de l’axe XML. Cependant, les espaces de noms globaux peuvent être utilisés avec les propriétés de l’axe XML. Utilisez un côlon pour séparer le préfixe XML namespace du nom de l’élément local. Vous trouverez ci-dessous un exemple :  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
