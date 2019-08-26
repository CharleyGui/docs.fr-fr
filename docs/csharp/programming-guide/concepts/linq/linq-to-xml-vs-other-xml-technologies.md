---
title: LINQ to XML, différences par rapport à Autres technologies XML3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 1cafa8b690afb753dfdb0301dc6a19f5f257e9c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591872"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML, différences par rapport à d'autres technologies XML
Cette rubrique compare [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aux technologies XML suivantes : <xref:System.Xml.XmlReader>, XSLT, MSXML et XmlLite. Ces informations peuvent vous aider à décider de la technologie à utiliser.  
  
 Pour une comparaison de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et du modèle DOM (Document Objet Model), consultez [LINQ to XML, différences par rapport à DOM (C#)](./linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML, différences par rapport à XmlReader  
 <xref:System.Xml.XmlReader> est un analyseur rapide, avant uniquement et sans mise en cache.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est implémenté sur <xref:System.Xml.XmlReader> et tous deux sont étroitement intégrés. Toutefois, vous pouvez également utiliser un <xref:System.Xml.XmlReader> seul.  
  
 Par exemple, supposez que vous créez un service Web qui analysera des centaines de documents XML par seconde et que les documents ont la même structure, ce qui signifie que vous n'avez qu'une seule implémentation du code à écrire pour analyser le XML. Dans ce cas, vous souhaiterez probablement utiliser un <xref:System.Xml.XmlReader> seul.  
  
 En revanche, si vous créez un système qui analyse beaucoup de petits documents XML et que chacun d’eux est différent, il est préférable de tirer parti des améliorations de productivité fournies par [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML, différences par rapport à XSLT  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et XSLT fournissent tous deux des fonctionnalités étendues de transformation de documents XML. XSLT est une approche déclarative basée sur des règles. Les programmeurs XSLT expérimentés écrivent du code XSLT dans un style de programmation fonctionnelle qui met l'accent sur une approche sans état. Les transformations peuvent être écrites à l'aide de fonctions pures implémentées sans effets secondaires. Cette approche fonctionnelle ou basée sur des règles est peu connue de la plupart des développeurs et son apprentissage peut être long et difficile.  
  
 XSLT peut être un système très productif qui génère des applications hautes performances. Par exemple, certaines grandes sociétés basées sur le Web utilisent XSLT afin de générer du code HTML à partir de code XML extrait de différents magasins de données. Le moteur XSLT managé compile XSLT en code CLR et, dans certains scénarios, offre des performances encore meilleures que le moteur XSLT natif.  
  
 Toutefois, XSLT ne tire pas parti des connaissances en C# et Visual Basic que de nombreux développeurs possèdent. Il exige des développeurs qu'ils écrivent du code dans un langage de programmation différent et complexe. L'utilisation de deux systèmes de développement non intégrés tels que C# (ou Visual Basic) et XSLT rend les systèmes logiciels plus difficiles à développer et à gérer.  
  
 Une fois que vous maîtrisez les expressions de requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], les transformations [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] représentent une technologie puissante et facile à utiliser. En résumé, vous formez votre document XML en utilisant la construction fonctionnelle, en extrayant des données de diverses sources, en construisant des objets <xref:System.Xml.Linq.XElement> de manière dynamique et en assemblant l'ensemble dans une nouvelle arborescence XML. La transformation peut générer un document complètement nouveau. La construction de transformations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est relativement facile et intuitive, et le code obtenu est bien lisible. Cela permet de réduire les coûts de développement et de maintenance.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] n'a pas pour but de remplacer XSLT. XSLT est toujours l'outil de prédilection pour les transformations XML complexes et centrées sur les documents, en particulier si la structure du document n'est pas bien définie.  
  
 XSLT présente l'avantage d'être une norme World Wide Web Consortium (W3C). Si vous avez l'obligation d'utiliser des technologies qui constituent des normes, il peut être plus judicieux d'utiliser XSLT.  
  
 Le code XSLT étant du code XML, il peut par conséquent être manipulé par programmation.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML, différences par rapport à MSXML  
 MSXML est une technologie compatible COM pour le traitement du code XML qui est fournie avec Microsoft Windows. MSXML fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT. Il contient également l'analyseur sans mise en cache et basé sur les événements SAX2.  
  
 MSXML offre de bonnes performances, est sécurisé par défaut dans la plupart des scénarios et est accessible dans Internet Explorer pour l'exécution de traitement XML du côté client dans les applications de style AJAX. MSXML peut être utilisé à partir de n’importe quel langage de programmation qui prend en charge COM, notamment C++, JavaScript et Visual Basic 6.0.  
  
 L'utilisation de MSXML n'est pas recommandée dans le code managé basé sur le Common Language Runtime (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML, différences par rapport à XmlLite  
 XmlLite est un analyseur de type extraction, avant uniquement et sans mise en cache. Les développeurs utilisent principalement XmlLite avec C++. Il est déconseillé aux développeurs d'utiliser XmlLite avec du code managé.  
  
 Le principal avantage de XmlLite est sa légèreté et sa rapidité d'analyse XML. De plus, il est sécurisé dans la plupart des scénarios. Sa surface de menace est très faible. Si vous devez analyser des documents non approuvés et que vous souhaitez vous protéger contre les attaques de type déni de service ou exposition de données, XmlLite peut constituer un bon choix.  
  
 XmlLite n'est pas intégré à [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Il ne procure pas les améliorations de productivité des programmeurs qui constituent le facteur de motivation associé à [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- [Bien démarrer (LINQ to XML)](./linq-to-xml-overview.md)
