---
title: Extension du DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 4a1a7af0e841601542a30c7bd3f71395faa6cb57
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287790"
---
# <a name="extending-the-dom"></a>Extension du DOM

Le .NET Framework Microsoft comprend un ensemble de classes de base qui fournit une implémentation du DOM (Document Objet Model) XML. L'objet <xref:System.Xml.XmlNode> et ses classes dérivées proposent des méthodes et des propriétés qui permettent la navigation, l'interrogation et la modification du contenu et de la structure d'un document XML.

Lors du chargement en mémoire de contenu XML à l'aide du DOM, les nœuds créés contiennent des informations telles que le nom de nœud, le type de nœud, etc. Il peut arriver que vous ayez besoin d'informations spécifiques sur les nœuds que les classes de base ne fournissent pas. Par exemple, il peut être utile de connaître le numéro de ligne et la position d'un nœud. Dans ce cas, vous pouvez faire dériver de nouvelles classes de classes DOM existantes et ajouter des fonctionnalités complémentaires.

La dérivation de nouvelles classes est soumise à deux indications générales :

- Il est recommandé de ne jamais faire dériver des classes de la classe <xref:System.Xml.XmlNode>. Il est plutôt conseillé de dériver des classes à partir de la classe qui correspond au type de nœud auquel vous vous intéressez. Par exemple, si vous souhaitez renvoyer des informations supplémentaires sur les nœuds d'attributs, vous pouvez dériver de la classe <xref:System.Xml.XmlAttribute>.

- À l'exception des méthodes de création de nœud, il est recommandé, lors de la substitution d'une fonction, de toujours appeler une version de base de la fonction et ensuite d'ajouter le complément de traitement éventuellement requis.

## <a name="creating-your-own-node-instances"></a>Création de vos propres instances de nœud

La classe <xref:System.Xml.XmlDocument> contient des méthodes de création de nœud. Quand un fichier XML est chargé, ces méthodes sont appelées afin de créer les nœuds. Vous pouvez les substituer de sorte que les instances de nœud soient créées au moment du chargement d'un document. Par exemple, si vous avez étendu la classe <xref:System.Xml.XmlElement>, la classe <xref:System.Xml.XmlDocument> est héritée et la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> remplacée.

L'exemple suivant montre comment substituer la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> afin de retourner votre implémentation de la classe <xref:System.Xml.XmlElement>.

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a>Extension d'une classe

Pour étendre une classe, faites-la dériver de l'une des classes DOM existantes. Ensuite, vous pouvez substituer n'importe quelle méthode ou propriété virtuelle de cette classe de base ou ajouter la vôtre.

Dans l'exemple suivant, une nouvelle classe est créée ; elle implémente la classe <xref:System.Xml.XmlElement> et l'interface <xref:System.Xml.IXmlLineInfo>. D'autres méthodes et propriétés sont définies pour permettre aux utilisateurs de recueillir des informations sur les lignes.

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a>Exemple

L’exemple suivant dénombre les éléments d’un document XML :

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a>Entrée

book.xml

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Output

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Gestionnaire d'événements de nœud

L'implémentation .NET Framework du DOM comprend également un système d'événements qui vous permet de recevoir et de gérer des événements lors de la modification de nœuds dans un document XML. L'utilisation des classes <xref:System.Xml.XmlNodeChangedEventHandler> et <xref:System.Xml.XmlNodeChangedEventArgs> vous permet de capturer des événements `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved` et `NodeRemoving`.

Le processus de gestion d'événements fonctionne exactement de la même façon dans les classes dérivées que dans les classes DOM d'origine.

Pour plus d’informations sur la gestion des événements de nœud, consultez [Événements](../../events/index.md) et <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Attributs par défaut et méthode CreateElement

Lors de la substitution de la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> dans une classe dérivée, les attributs par défaut ne sont pas ajoutés lorsque vous créez de nouveaux éléments pendant la modification du document. Ce problème ne se pose que lors de la modification. Puisque la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> est responsable de l'ajout d'attributs par défaut à un objet <xref:System.Xml.XmlDocument>, vous devez coder cette fonctionnalité dans la méthode <xref:System.Xml.XmlDocument.CreateElement%2A>. Si vous chargez un objet <xref:System.Xml.XmlDocument> qui comporte des attributs par défaut, ceux-ci sont gérés correctement. Pour plus d'informations sur les attributs par défaut, voir [Création de nouveaux attributs pour des éléments du DOM](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
