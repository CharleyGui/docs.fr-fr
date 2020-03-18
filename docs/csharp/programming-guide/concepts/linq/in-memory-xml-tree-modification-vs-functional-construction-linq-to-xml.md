---
title: Modification de l’arbre XML in-Memory vs Construction fonctionnelle (LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484557"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Modification de l’arbre XML in-Memory vs Construction fonctionnelle (LINQ à XML) (C)
La modification d'une arborescence XML sur place est une approche traditionnelle de la modification de la forme d'un document XML. Une application ordinaire charge un document dans un magasin de données tel que DOM ou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], utilise une interface de programmation pour insérer des nœuds, supprimer des nœuds ou modifier le contenu de nœuds, puis enregistre le code XML dans un fichier ou le transmet sur un réseau.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permet d’adopter une autre approche utile dans de nombreux scénarios : la *construction fonctionnelle*. La construction fonctionnelle traite la modification des données comme un problème de transformation plutôt que comme une manipulation détaillée d'un magasin de données. Si vous pouvez prendre une représentation de données et la transformer de manière efficace d'une forme en une autre, cela équivaut à prendre un magasin de données et à le manipuler d'une certaine manière de sorte qu'il prenne une autre forme. L’une des clés de l’approche de construction fonctionnelle consiste à passer les résultats des requêtes à des constructeurs <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>.  
  
 Dans de nombreux cas, vous pouvez écrire du code transformationnel en beaucoup moins de temps qu'il ne faudrait pour manipuler le magasin de données, et ce code est plus robuste et plus facile à maintenir. Dans ces cas-là, bien que l'approche transformationnelle puisse nécessiter davantage de puissance de traitement, elle est plus efficace pour la modification des données. Si le développeur a une bonne connaissance de l'approche fonctionnelle, le code résultant est bien souvent plus facile à comprendre. Il est facile de trouver le code qui modifie chaque partie de l'arborescence.  
  
 L'approche qui consiste à modifier une arborescence XML sur place est plus connue des programmeurs DOM, tandis que le code écrit à l'aide de l'approche fonctionnelle peut sembler plus obscur aux yeux d'un développeur qui ne s'est pas encore familiarisé avec cette approche. Si vous ne devez modifier qu'une petite partie d'une grande arborescence XML, la modification de l'arborescence sur place nécessite généralement moins de temps processeur.  
  
 Cette rubrique fournit un exemple qui est implémenté avec les deux approches.  
  
## <a name="transforming-attributes-into-elements"></a>Transformation d'attributs en éléments  
 Pour cet exemple, supposez que vous souhaitez modifier le document XML simple suivant de sorte que les attributs deviennent des éléments. Cette section présente tout d'abord l'approche classique de modification sur place. Elle illustre ensuite l'approche de construction fonctionnelle.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Modification de l'arborescence XML  
 Vous pouvez écrire des procédures de code pour créer des éléments à partir des attributs, puis supprimer les attributs comme suit :  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Approche de construction fonctionnelle  
 Par contraste, une approche fonctionnelle consiste à écrire du code pour former une nouvelle arborescence, à choisir des éléments et des attributs dans l'arborescence source et à les transformer en conséquence à mesure qu'ils sont ajoutés à la nouvelle arborescence. L'approche fonctionnelle ressemble à ceci :  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Cet exemple renvoie le même code XML que le premier exemple. Toutefois, remarquez que vous pouvez observer la structure résultante du nouveau code XML avec l'approche fonctionnelle. Vous pouvez voir la création de l'élément `Root`, le code qui extrait l'élément `Child1` de l'arborescence source et le code qui transforme les attributs de l'arborescence source en éléments dans la nouvelle arborescence.  
  
 Dans ce cas, l'exemple fonctionnel n'est pas plus court que le premier exemple et n'est pas vraiment plus simple non plus. Toutefois, si vous devez apporter de nombreuses modifications à une arborescence XML, l'approche non fonctionnelle devient assez complexe et quelque peu abstruse. En revanche, avec l'approche fonctionnelle, il suffit toujours de former le code XML souhaité, d'incorporer les requêtes et les expressions, puis d'extraire le contenu souhaité. L'approche fonctionnelle génère du code qui est plus facile à maintenir.  
  
 Notez que dans ce cas les performances obtenues par le biais de l'approche fonctionnelle seraient inférieures à celles de l'approche par manipulation. Le principal problème est que l'approche fonctionnelle crée davantage d'objets à courte durée de vie. Toutefois, le compromis est que cette approche autorise une meilleure productivité du programmeur.  
  
 Il s'agit d'un exemple très simple, mais qui permet d'illustrer les différences de philosophie de ces deux approches. L'approche fonctionnelle génère des gains de productivité supérieurs pour la transformation des grands documents XML.  
  