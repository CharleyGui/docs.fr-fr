---
title: 'Procédure : effectuer le streaming de fragments XML avec accès aux informations d’en-tête'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 8d0543ff5a772768292c0e3117f41bea9367d23a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397685"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Comment : diffuser des fragments XML en continu avec accès aux informations d’en-tête (Visual Basic)
Vous devez parfois lire des fichiers XML arbitrairement volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible. Si vous tentez de remplir une arborescence XML avec un grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive). Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.  
  
 L'une des options consiste à écrire votre application à l'aide de <xref:System.Xml.XmlReader>. Toutefois, vous souhaiterez peut-être utiliser LINQ pour interroger l’arborescence XML. Si tel est le cas, vous pouvez écrire votre propre méthode d'axe personnalisée. Pour plus d’informations, consultez [Comment : écrire une méthode d’axe LINQ to XML (Visual Basic)](how-to-write-a-linq-to-xml-axis-method.md).  
  
 Pour écrire votre propre méthode d'axe personnalisée, vous écrivez une petite méthode qui utilise l'objet <xref:System.Xml.XmlReader> pour lire les nœuds jusqu'à atteindre l'un des nœuds qui vous intéressent. La méthode appelle ensuite <xref:System.Xml.Linq.XNode.ReadFrom%2A>, qui lit à partir de l'objet <xref:System.Xml.XmlReader> et instancie un fragment XML. Vous pouvez ensuite écrire des requêtes LINQ sur votre méthode d'axe personnalisée.  
  
 Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document. Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence. Notez que si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire.  
  
## <a name="example"></a>Exemple  
 Le problème peut parfois être un peu plus épineux. Dans le document XML suivant, le consommateur de votre méthode d'axe personnalisée doit également connaître le nom du client auquel appartient chaque élément.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 L'approche utilisée dans cet exemple consiste à rechercher ces informations d'en-tête, à les enregistrer, puis à générer une petite arborescence XML qui contient à la fois les informations d'en-tête et le détail que vous énumérez. La méthode d'axe produit ensuite cette nouvelle petite arborescence XML. La requête a alors accès aux informations d'en-tête et aux informations de détail.  
  
 Cette approche présente un faible encombrement mémoire. À mesure que chaque fragment XML de détail est produit, aucune référence au fragment précédent n'est conservée et il est disponible pour le garbage collection. Notez que cette technique crée de nombreux objets à courte durée de vie sur la pile.  
  
 L'exemple suivant montre comment implémenter et utiliser une méthode d'axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par l'URI. Cet axe personnalisé est écrit spécifiquement de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document `Source.xml` ci-dessus. Il s'agit d'une implémentation simpliste. Une implémentation plus robuste serait préparée à analyser un document non valide.  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
    End Sub  
  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](advanced-linq-to-xml-programming.md)
