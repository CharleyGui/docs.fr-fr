---
title: Modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle-LINQ to XML
description: Consultez des exemples de deux approches différentes pour modifier des arborescences XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552420"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a>Modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle (LINQ to XML)

La modification d'une arborescence XML sur place est une approche traditionnelle de la modification de la forme d'un document XML. Une application typique charge un document dans un magasin de données tel que DOM ou LINQ to XML ; utilise une interface de programmation pour insérer ou supprimer des nœuds, ou modifier leur contenu ; puis enregistre le code XML dans un fichier ou le transmet sur un réseau.

LINQ to XML offre une autre approche utile dans de nombreux scénarios : la *construction fonctionnelle*. La construction fonctionnelle traite la modification des données comme un problème de transformation plutôt que comme une manipulation détaillée d'un magasin de données. Si vous pouvez prendre une représentation de données et la transformer de manière efficace d'une forme en une autre, cela équivaut à prendre un magasin de données et à le manipuler d'une certaine manière de sorte qu'il prenne une autre forme. L’une des clés de l’approche de construction fonctionnelle consiste à passer les résultats des requêtes à des constructeurs <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>.

Dans de nombreux cas, vous pouvez écrire le code de transformation dans une fraction du temps qu’il faudrait pour manipuler le magasin de données, et le code obtenu est plus robuste et plus facile à gérer. Dans ce cas, bien que l’approche transformationnelle puisse nécessiter davantage de puissance de traitement, il est plus efficace de modifier les données. Si un développeur est familiarisé avec l’approche fonctionnelle, le code résultant dans de nombreux cas est plus facile à comprendre et il est facile de trouver le code qui modifie chaque partie de l’arborescence.

L’approche qui consiste à modifier une arborescence XML sur place est plus familière à de nombreux programmeurs DOM, tandis que le code écrit à l’aide de l’approche fonctionnelle peut sembler peu familier à un développeur qui n’a pas encore compris cette approche. Si vous ne devez modifier qu'une petite partie d'une grande arborescence XML, la modification de l'arborescence sur place nécessite généralement moins de temps processeur.

Cet article fournit des exemples des deux approches. Supposons que vous souhaitiez modifier le document XML simple suivant de sorte que les attributs deviennent des éléments :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

Le premier des exemples suivants utilise l’approche traditionnelle de modification sur place, tandis que la seconde utilise l’approche de construction fonctionnelle.

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a>Exemple : transformer des attributs en éléments avec l’approche sur place traditionnelle

Vous pouvez écrire des procédures de code pour créer des éléments à partir des attributs, puis supprimer les attributs comme suit :

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

Cet exemple produit la sortie suivante :

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a>Exemple : transformer des attributs en éléments avec l’approche de construction fonctionnelle

En revanche, une approche fonctionnelle consiste à coder pour former une nouvelle arborescence, à choisir des éléments et des attributs à partir de l’arborescence source et à les transformer en fonction des besoins lorsqu’ils sont ajoutés à la nouvelle arborescence.

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

Cet exemple renvoie le même code XML que le premier exemple. Toutefois, remarquez que vous pouvez observer la structure résultante du nouveau code XML avec l'approche fonctionnelle. Vous pouvez voir la création de l'élément `Root`, le code qui extrait l'élément `Child1` de l'arborescence source et le code qui transforme les attributs de l'arborescence source en éléments dans la nouvelle arborescence.

Dans ce cas, l’exemple fonctionnel n’est ni plus rapide ni plus simple que le premier exemple. Toutefois, si vous avez de nombreuses modifications à apporter à une arborescence XML, l’approche procédurale devient assez complexe et quelque peu abstruse. En revanche, avec l'approche fonctionnelle, il suffit toujours de former le code XML souhaité, d'incorporer les requêtes et les expressions, puis d'extraire le contenu souhaité. L'approche fonctionnelle génère du code qui est plus facile à maintenir.

Notez que dans ce cas les performances obtenues par le biais de l'approche fonctionnelle seraient inférieures à celles de l'approche par manipulation. Le principal problème est que l’approche fonctionnelle crée davantage d’objets éphémères. Toutefois, le compromis est que cette approche autorise une meilleure productivité du programmeur.

Il s'agit d'un exemple très simple, mais qui permet d'illustrer les différences de philosophie de ces deux approches. L'approche fonctionnelle génère des gains de productivité supérieurs pour la transformation des grands documents XML.
