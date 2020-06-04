---
title: 'Comment : supprimer une ressource système'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403496"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="e4dee-102">Comment : supprimer une ressource système (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4dee-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="e4dee-103">Vous pouvez utiliser un `Using` bloc pour garantir que le système supprime une ressource quand votre code quitte le bloc.</span><span class="sxs-lookup"><span data-stu-id="e4dee-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="e4dee-104">Cela est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou que d’autres composants souhaitent également utiliser.</span><span class="sxs-lookup"><span data-stu-id="e4dee-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="e4dee-105">Pour supprimer une connexion de base de données lorsque votre code en a terminé</span><span class="sxs-lookup"><span data-stu-id="e4dee-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="e4dee-106">Veillez à inclure l' [instruction Imports appropriée (espace de noms et type .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour la connexion de base de données au début de votre fichier source (dans ce cas, <xref:System.Data.SqlClient> ).</span><span class="sxs-lookup"><span data-stu-id="e4dee-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="e4dee-107">Créez un `Using` bloc avec les `Using` `End Using` instructions et.</span><span class="sxs-lookup"><span data-stu-id="e4dee-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="e4dee-108">Dans le bloc, placez le code qui gère la connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="e4dee-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="e4dee-109">Déclarez la connexion et créez une instance de celle-ci dans le cadre de l' `Using` instruction.</span><span class="sxs-lookup"><span data-stu-id="e4dee-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="e4dee-110">Le système supprime la ressource, quelle que soit la façon dont vous quittez le bloc, y compris le cas d’une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="e4dee-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="e4dee-111">Notez que vous ne pouvez pas accéder `sqc` depuis l’extérieur du `Using` bloc, car sa portée est limitée au bloc.</span><span class="sxs-lookup"><span data-stu-id="e4dee-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="e4dee-112">Vous pouvez utiliser cette même technique sur une ressource système telle qu’un handle de fichier ou un wrapper COM.</span><span class="sxs-lookup"><span data-stu-id="e4dee-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="e4dee-113">Vous utilisez un `Using` bloc lorsque vous souhaitez être sûr de conserver la ressource disponible pour d’autres composants une fois que vous avez quitté le `Using` bloc.</span><span class="sxs-lookup"><span data-stu-id="e4dee-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dee-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4dee-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="e4dee-115">Workflow de contrôle</span><span class="sxs-lookup"><span data-stu-id="e4dee-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="e4dee-116">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="e4dee-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="e4dee-117">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="e4dee-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="e4dee-118">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="e4dee-118">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="e4dee-119">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="e4dee-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="e4dee-120">Instruction using</span><span class="sxs-lookup"><span data-stu-id="e4dee-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
