---
title: 'Comment : remplir une arborescence XML à partir du système de fichiers'
ms.date: 07/20/2015
ms.assetid: 34eec79e-7945-4ba8-9f74-d05bb8ec67f6
ms.openlocfilehash: 5a4c7eaea91db54afcd91d85745dfec27cbabb8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344474"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-visual-basic"></a><span data-ttu-id="9bd31-102">How to: Populate an XML Tree from the File System (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bd31-102">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>
<span data-ttu-id="9bd31-103">Une application courante et utile des arborescences XML consiste à les utiliser en tant que banque de données nom/valeur hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="9bd31-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="9bd31-104">Vous pouvez remplir une arborescence XML avec des données hiérarchiques, puis les interroger, les transformer et, si nécessaire, les sérialiser.</span><span class="sxs-lookup"><span data-stu-id="9bd31-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="9bd31-105">Dans ce scénario, une grande partie de la sémantique spécifique au langage XML, telle que les espaces de noms et le comportement d'espace blanc, n'est pas importante.</span><span class="sxs-lookup"><span data-stu-id="9bd31-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="9bd31-106">Au lieu de cela, vous utilisez l’arborescence XML en tant que petite base de données hiérarchique en mémoire et à utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="9bd31-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd31-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="9bd31-107">Example</span></span>  
 <span data-ttu-id="9bd31-108">L’exemple suivant remplit une arborescence XML à partir du système de fichiers à l’aide de la récursivité.</span><span class="sxs-lookup"><span data-stu-id="9bd31-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="9bd31-109">Il interroge ensuite l'arborescence XML et calcule le total de tous les fichiers dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="9bd31-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```vb  
Module Module1  
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement  
        Dim di As DirectoryInfo = New DirectoryInfo(source)  
        Return <Dir Name=<%= di.Name %>>  
                   <%= From d In Directory.GetDirectories(source) _  
                       Select CreateFileSystemXmlTree(d) %>  
                   <%= From fi In di.GetFiles() _  
                       Select <File>  
                                  <Name><%= fi.Name %></Name>  
                                  <Length><%= fi.Length %></Length>  
                              </File> %>  
               </Dir>  
    End Function  
  
    Sub Main()  
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")  
        Console.WriteLine(fileSystemTree)  
        Console.WriteLine("------")  
        Dim totalFileSize As Long = _  
            ( _  
                From f In fileSystemTree...<File> _  
                Select CLng(f.<Length>(0)) _  
            ).Sum()  
        Console.WriteLine("Total File Size:{0}", totalFileSize)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9bd31-110">Cet exemple produit une sortie semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="9bd31-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bd31-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bd31-111">See also</span></span>

- [<span data-ttu-id="9bd31-112">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bd31-112">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
