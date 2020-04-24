---
title: Implémentation de comportements discrétionnaires dans la classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
ms.openlocfilehash: b37cb0f4bf9a85053d70d549ae005c7d50a50bc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710802"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implémentation de comportements discrétionnaires dans la classe XslTransform

> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).

Les comportements discrétionnaires sont décrits comme des comportement listés dans la [recommandation du World Wide Web Consortium (W3C) sur XSLT (XSL Transformations) Version 1.0](https://www.w3.org/TR/1999/REC-xslt-19991116), où le fournisseur d’implémentation choisit une option parmi plusieurs possibles pour gérer une situation. Par exemple, dans la section 7.3 sur la création d'instructions de traitement, la recommandation du W3C précise que la création de nœuds autres que des nœuds de texte lors d'une instanciation du contenu de `xsl:processing-instruction` correspond à une erreur. Pour certains problèmes, le W3C indique la décision à prendre si le processeur décide de récupérer l'erreur. Pour le problème donné dans la section 7.3, le W3C indique que l'implémentation peut récupérer cette erreur en ignorant les nœuds et leur contenu.

Par conséquent, pour chacun des comportements discrétionnaires autorisés par le W3C, le tableau suivant liste les comportements discrétionnaires implémentés pour l’implémentation du .NET Framework de la classe <xref:System.Xml.Xsl.XslTransform>, ainsi que la section de la recommandation du W3C sur XSLT 1.0 traitant de ce problème.

|Problème|Comportement|Section|
|-------------|--------------|-------------|
|Un nœud de texte correspond à la fois à `xsl:strip-space` et à `xsl:preserve-space`.|Recover|3.4|
|Un nœud source correspond à plusieurs règles de modèle.|Recover|5.5|
|Un URI (Uniform Resource Identifier) d'espace de noms est déclaré comme étant un alias pour plusieurs URI d'espaces de noms dont la priorité d'importation est identique.|Recover|7.1.1|
|L'attribut de nom dans `xsl:attribute` et `xsl:element` généré à partir d'un modèle de valeur d'attribut n'est pas un nom qualifié (QName) valide.|Exception levée|7.1.2 et 7.1.3|
|L'ajout d'un attribut à un élément après l'ajout de nœuds enfants au nœud élément.|Recover|7.1.3|
|Ajout d'un attribut à autre chose qu'à un nœud d'élément.|Recover|7.1.3|
|L'instanciation du contenu de l'élément `xsl:attribute` n'est pas un nœud de texte.|Recover|7.1.3|
|Deux ensembles d'attributs ont la même priorité d'importation et le même nom développé. Les deux ont le même attribut et il n'y a pas d'autre ensemble d'attributs contenant l'attribut commun avec le même nom et une importance supérieure.|Recover|7.1.4|
|L'attribut de nom `xsl:processing-instruction` ne produit pas un NCName et une cible d'instruction de traitement.|Recover|7.3|
|L'instanciation du contenu de `xsl:processing-instruction` crée des nœuds autres que des nœuds de texte.|Recover|7.3|
|Les résultats de l'instanciation du contenu de `xsl:processing-instruction` contiennent la chaîne « `?>` ».|Recover|7.3|
|Les résultats de l'instanciation du contenu de `xsl:comment` contiennent la chaîne « -- » ou se terminent par « - ».|Recover|7.4|
|Les résultats de l'instanciation du contenu de `xsl:comment` créent des nœuds autres que des nœuds de texte.|Recover|7.4|
|Le modèle d'un élément de liaison de variables retourne un nœud d'attribut ou un nœud d'espace de noms.|Recover|11.2|
|Une erreur se produit lors de l'extraction de la ressource à partir de l'URI passé dans la fonction de document.|Exception levée|12.1|
|La référence URI de la fonction de document contient un identificateur de fragment, et une erreur se produit lors du traitement de ce dernier.|Exception levée|12.1|
|Il existe plusieurs attributs portant le même nom qui ne sont pas intitulés `cdata-section-elements` dans `xls:output`, et ces attributs ont la même priorité d'importation.|Recover|16|
|Le processeur ne prend pas en charge la valeur d'encodage de caractères octroyée dans l'attribut `encoding` de l'élément `xsl:output`.|Recover|16,1|
|`disable-output-escaping` s'utilise pour un nœud de texte et ce nœud est utilisé pour créer autre chose qu'un nœud de texte dans l'arborescence résultat.|L'attribut `disable-output-escaping` est ignoré.|16.4|
|Conversion d'un fragment d'arborescence résultat en un nombre ou une chaîne si le fragment d'arborescence résultat contient un nœud de texte dont la production littérale des caractères en sortie est activée.|Ignoré|16.4|
|La production littérale des caractères en sortie est désactivée pour les caractères qui ne peuvent pas être représentés dans l'encodage utilisé par le processeur XSLT pour la sortie.|Ignoré|16.4|
|Ajout d'un nœud d'espace de noms à un élément après que les enfants ou les attributs ont été ajoutés à ce dernier.|Recover|Errata e25|
|`xsl:number` est une valeur NaN, infinie ou inférieure à 0,5.|Recover|Errata e24|
|La collection de nœuds du second argument de la fonction de document est vide et la référence URI est relative.|Recover|Errata e14|

Vous trouverez les sections sur les erreurs dans [XSL Transformations (XSLT) Version 1.0 Specification Errata](https://www.w3.org/1999/11/REC-xslt-19991116-errata/) du W3C.

## <a name="custom-defined-implementation-behaviors"></a>Comportements d'implémentation personnalisés

Certains comportements sont spécifiques à l'implémentation de la classe <xref:System.Xml.Xsl.XslTransform>. Cette section présente l'implémentation propre au fournisseur de `xsl:sort` et les fonctionnalités facultatives prises en charge par la classe <xref:System.Xml.Xsl.XslTransform>.

## <a name="xslsort"></a>xsl:sort

Lors de l'utilisation d'une transformation à trier, la recommandation du W3C sur XSLT 1.0 établit des observations. Il s'agit de :

- Deux processeurs XSLT peuvent être des processeurs conformes, mais ils peuvent effectuer un tri différent.

- Tous les processeurs XSLT ne prennent pas en charge les mêmes langages.

- En ce qui concerne les langages, le tri effectué par des processeurs distincts peut varier sur un langage spécifique, non spécifié dans le `xsl:sort.`.

Le tableau suivant montre le comportement de tri implémenté pour chaque type de données dans l'implémentation .NET Framework d'une transformation utilisant l'objet <xref:System.Xml.Xsl.XslTransform> :

|Type de données|Comportement de tri|
|---------------|----------------------|
|Texte|Les données sont triées en utilisant la méthode String.Compare du Common Language Runtime (CLR) ainsi que les paramètres régionaux culturels. Lorsque les données sont de type « texte », le tri dans la classe <xref:System.Xml.Xsl.XslTransform> se comporte de la même façon que les comportements de comparaison de chaînes du Common Language Runtime.|
|Number|Les valeurs numériques sont traitées comme des nombres XPath (XML Path Language) et sont triées en fonction des détails présentés dans [XML Path Language (XPath) Version 1.0 Recommendation, Section 3.5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers) du W3C.|

## <a name="optional-features-supported"></a>Fonctionnalités facultatives prises en charge

Le tableau suivant présente les fonctionnalités facultatives à implémenter pour un processeur XSLT et qui sont implémentées dans la classe <xref:System.Xml.Xsl.XslTransform>.

|Fonctionnalité|Emplacement de référence|Notes|
|-------------|------------------------|-----------|
|Attribut `disable-output-escaping` sur les balises `<xsl:text...>` et `<xsl:value-of...>`.|Recommandation du W3C sur XSLT 1.0, <br /><br /> Section 16.4|L'attribut `disable-output-escaping` est ignoré lorsque l'élément `xsl:text` ou `xsl:value-of` est utilisé dans un élément `xsl:comment`, `xsl:processing-instruction` ou `xsl:attribute`.<br /><br /> Les fragments d'arborescence résultat qui contiennent du texte et la sortie de texte ayant fait l'objet d'un échappement ne sont pas pris en charge.<br /><br /> L'attribut disable-output-escaping est ignoré lors de sa transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.|

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Xsl.XslTransform>
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Transformations XSLT avec la classe XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [XPathNavigator dans les transformations](xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDataDocument dans XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Entrée XmlDocument dans XslTransform](xmldocument-input-to-xsltransform.md)
