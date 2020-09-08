---
title: LINQ to XML différences par rapport à d’autres technologies XML
description: Découvrez comment LINQ to XML compare à XSLT, MSXML et XmlLite pour offrir de meilleures options technologiques.
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: ac118543bd1101e50edfcf99a609a715b885bfbd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553479"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML différences par rapport à d’autres technologies XML

Cet article compare LINQ to XML aux technologies XML suivantes : <xref:System.Xml.XmlReader> , XSLT, MSXML et XmlLite. Ces informations peuvent vous aider à choisir les technologies à utiliser.

Pour une comparaison entre les LINQ to XML et le Document Object Model (DOM), consultez [LINQ to XML et DOM](linq-xml-vs-dom.md).

## <a name="linq-to-xml-vs-xmlreader"></a>Comparaison de LINQ to XML et de XmlReader

<xref:System.Xml.XmlReader> est un analyseur rapide, avant uniquement et sans mise en cache.

LINQ to XML est implémentée en plus de <xref:System.Xml.XmlReader> , et elles sont étroitement intégrées. Toutefois, vous pouvez également utiliser <xref:System.Xml.XmlReader> directement.

Supposons, par exemple, que vous génériez un service Web qui analysera des centaines de documents XML par seconde et que les documents ont la même structure, ce qui signifie que vous n’aurez à écrire qu’une seule implémentation du code pour analyser le code XML. Dans ce cas, vous souhaiterez probablement utiliser <xref:System.Xml.XmlReader> directement.

En revanche, si vous créez un système qui analyse un grand nombre de documents XML plus petits et que chacun d’eux est différent, vous souhaiterez tirer parti des améliorations de productivité fournies par LINQ to XML.

## <a name="linq-to-xml-vs-xslt"></a>Comparaison de LINQ to XML et XSLT

LINQ to XML et XSLT fournissent des fonctionnalités de transformation de documents XML étendues. XSLT est une approche déclarative basée sur des règles. Les programmeurs XSLT expérimentés écrivent du code XSLT dans un style de programmation fonctionnelle qui met l'accent sur une approche sans état. Les transformations peuvent être écrites à l'aide de fonctions pures implémentées sans effets secondaires. Cette approche fonctionnelle ou basée sur des règles est peu connue de la plupart des développeurs et son apprentissage peut être long et difficile.

XSLT peut être un système productif qui génère des applications hautes performances. Par exemple, certaines grandes entreprises Web utilisent XSLT pour générer du code HTML à partir de code XML extrait de différents types de magasins de données. Le moteur XSLT managé compile XSLT en code common language runtime (CLR) et s’exécute encore mieux dans certains scénarios que le moteur XSLT natif.

Toutefois, XSLT ne tire pas parti des connaissances en C# et en Visual Basic que de nombreux développeurs ont. Il exige des développeurs qu'ils écrivent du code dans un langage de programmation différent et complexe. L'utilisation de deux systèmes de développement non intégrés tels que C# (ou Visual Basic) et XSLT rend les systèmes logiciels plus difficiles à développer et à gérer.

Une fois que vous avez masterisé LINQ to XML expressions de requête, les transformations LINQ to XML sont une technologie puissante qui est facile à utiliser. En résumé, vous formez votre document XML en utilisant la construction fonctionnelle, en extrayant des données de diverses sources, en construisant des objets <xref:System.Xml.Linq.XElement> de manière dynamique et en assemblant l'ensemble dans une nouvelle arborescence XML. La transformation peut générer un document complètement nouveau. La construction de transformations dans LINQ to XML est relativement facile et intuitive, et le code obtenu est lisible. Cela permet de réduire les coûts de développement et de maintenance.

LINQ to XML n’est pas destiné à remplacer XSLT. XSLT est toujours l’outil de prédilection pour les transformations XML complexes et centrées sur les documents, en particulier si la structure du document n’est pas bien définie.

XSLT présente l'avantage d'être une norme World Wide Web Consortium (W3C). Si vous avez l'obligation d'utiliser des technologies qui constituent des normes, il peut être plus judicieux d'utiliser XSLT.

XSLT est du XML et c’est pour cette raison qu’il peut être manipulé par programmation.

## <a name="linq-to-xml-vs-msxml"></a>Comparaison de LINQ to XML et MSXML

MSXML est la technologie COM pour le traitement de données XML qui est fournie avec Microsoft Windows. MSXML fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT. Il contient également l'analyseur sans mise en cache et basé sur les événements SAX2.

MSXML fonctionne bien, est sécurisé par défaut dans la plupart des scénarios et est accessible dans Internet Explorer pour effectuer le traitement XML côté client dans les applications de style AJAX. MSXML peut être utilisé à partir de n’importe quel langage de programmation qui prend en charge COM, notamment C++, JavaScript et Visual Basic 6.0.

MSXML n’est pas recommandé pour une utilisation dans du code managé basé sur le CLR.

## <a name="linq-to-xml-vs-xmllite"></a>Comparaison de LINQ to XML et de XmlLite

XmlLite est un analyseur de type extraction, avant uniquement et sans mise en cache. Les développeurs utilisent principalement XmlLite avec C++. Il n’est pas recommandé pour les développeurs d’utiliser XmlLite avec du code managé.

Le principal avantage de XmlLite est qu’il s’agit d’un analyseur XML léger et rapide qui est sécurisé dans la plupart des scénarios. Sa surface de menace est petite. Si vous devez analyser des documents non approuvés et que vous souhaitez vous protéger contre les attaques de type déni de service ou exposition de données, XmlLite peut constituer un bon choix.

XmlLite n’est pas intégré à LINQ (Language-Integrated Query). Elle ne produit pas les améliorations de productivité des programmeurs qui sont la force de motivation derrière LINQ.

## <a name="see-also"></a>Voir aussi

- [Présentation de LINQ to XML](linq-xml-overview.md)
