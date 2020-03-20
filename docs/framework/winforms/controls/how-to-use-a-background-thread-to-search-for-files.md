---
title: "Comment : utiliser un thread d'arrière-plan pour rechercher des fichiers"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Multithreaded Windows Forms Control sample [Windows Forms]
- custom controls [Windows Forms], multithreading
- threading [Windows Forms], custom controls
- custom controls [Windows Forms], samples
ms.assetid: 7fe3956f-5b8f-4f78-8aae-c9eb0b28f13a
ms.openlocfilehash: a58792ef6356c84d7d0c195eed21269e4036aacc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182088"
---
# <a name="how-to-use-a-background-thread-to-search-for-files"></a><span data-ttu-id="95329-102">Comment : utiliser un thread d'arrière-plan pour rechercher des fichiers</span><span class="sxs-lookup"><span data-stu-id="95329-102">How to: Use a Background Thread to Search for Files</span></span>
<span data-ttu-id="95329-103">Le <xref:System.ComponentModel.BackgroundWorker> composant remplace et ajoute <xref:System.Threading> des fonctionnalités à l’espace de nom; cependant, <xref:System.Threading> l’espace de nom est conservé pour la compatibilité vers l’arrière et l’utilisation future, si vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="95329-103">The <xref:System.ComponentModel.BackgroundWorker> component replaces and adds functionality to the <xref:System.Threading> namespace; however, the <xref:System.Threading> namespace is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="95329-104">Pour plus d’informations, voir [Aperçu des composants de BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95329-104">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>

 <span data-ttu-id="95329-105">Windows Forms utilise le modèle d’appartement à threads unique (STA) parce que Windows Forms est basé sur des fenêtres Win32 indigènes qui sont intrinsèquement filées par appartement.</span><span class="sxs-lookup"><span data-stu-id="95329-105">Windows Forms uses the single-threaded apartment (STA) model because Windows Forms is based on native Win32 windows that are inherently apartment-threaded.</span></span> <span data-ttu-id="95329-106">Le modèle STA implique qu’une fenêtre peut être créée sur n’importe quel thread, mais elle ne peut pas changer de thread une fois créé, et tous les appels de fonction à elle doivent se produire sur son fil de création.</span><span class="sxs-lookup"><span data-stu-id="95329-106">The STA model implies that a window can be created on any thread, but it cannot switch threads once created, and all function calls to it must occur on its creation thread.</span></span> <span data-ttu-id="95329-107">En dehors des formulaires Windows, les classes du cadre .NET utilisent le modèle de threading gratuit.</span><span class="sxs-lookup"><span data-stu-id="95329-107">Outside Windows Forms, classes in the .NET Framework use the free threading model.</span></span> <span data-ttu-id="95329-108">Pour plus d’informations sur le threading dans le cadre .NET, voir [Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="95329-108">For information about threading in the .NET Framework, see [Threading](../../../standard/threading/index.md).</span></span>

 <span data-ttu-id="95329-109">Le modèle STA exige que toutes les méthodes sur un contrôle qui doivent être appelées de l’extérieur du fil de création du contrôle doivent être mobilisées pour (exécuté sur) le fil de création du contrôle.</span><span class="sxs-lookup"><span data-stu-id="95329-109">The STA model requires that any methods on a control that need to be called from outside the control's creation thread must be marshaled to (executed on) the control's creation thread.</span></span> <span data-ttu-id="95329-110">La classe <xref:System.Windows.Forms.Control> de base<xref:System.Windows.Forms.Control.Invoke%2A> <xref:System.Windows.Forms.Control.BeginInvoke%2A>fournit <xref:System.Windows.Forms.Control.EndInvoke%2A>plusieurs méthodes ( , , et ) à cet effet.</span><span class="sxs-lookup"><span data-stu-id="95329-110">The base class <xref:System.Windows.Forms.Control> provides several methods (<xref:System.Windows.Forms.Control.Invoke%2A>, <xref:System.Windows.Forms.Control.BeginInvoke%2A>, and <xref:System.Windows.Forms.Control.EndInvoke%2A>) for this purpose.</span></span> <span data-ttu-id="95329-111"><xref:System.Windows.Forms.Control.Invoke%2A>fait des appels de méthode synchrones; <xref:System.Windows.Forms.Control.BeginInvoke%2A> fait des appels de méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="95329-111"><xref:System.Windows.Forms.Control.Invoke%2A> makes synchronous method calls; <xref:System.Windows.Forms.Control.BeginInvoke%2A> makes asynchronous method calls.</span></span>

 <span data-ttu-id="95329-112">Si vous utilisez la multithreading dans votre contrôle pour les tâches à forte intensité de ressources, l’interface utilisateur peut rester réactive pendant qu’un calcul à forte intensité de ressources s’exécute sur un thread d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="95329-112">If you use multithreading in your control for resource-intensive tasks, the user interface can remain responsive while a resource-intensive computation executes on a background thread.</span></span>

 <span data-ttu-id="95329-113">L’échantillon`DirectorySearcher`suivant ( ) montre un contrôle multithreaded Windows Forms qui utilise un thread d’arrière-plan pour rechercher de façon récursiveusement un répertoire pour les fichiers correspondant à une chaîne de recherche spécifiée, puis remplit une boîte de liste avec le résultat de recherche.</span><span class="sxs-lookup"><span data-stu-id="95329-113">The following sample (`DirectorySearcher`) shows a multithreaded Windows Forms control that uses a background thread to recursively search a directory for files matching a specified search string and then populates a list box with the search result.</span></span> <span data-ttu-id="95329-114">Les concepts clés illustrés par l’échantillon sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="95329-114">The key concepts illustrated by the sample are as follows:</span></span>

- <span data-ttu-id="95329-115">`DirectorySearcher`commence un nouveau thread pour effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="95329-115">`DirectorySearcher` starts a new thread to perform the search.</span></span> <span data-ttu-id="95329-116">Le thread exécute `ThreadProcedure` la méthode qui à `RecurseDirectory` son tour appelle la méthode d’aide pour faire la recherche réelle et de remplir la boîte de liste.</span><span class="sxs-lookup"><span data-stu-id="95329-116">The thread executes the `ThreadProcedure` method that in turn calls the helper `RecurseDirectory` method to do the actual search and to populate the list box.</span></span> <span data-ttu-id="95329-117">Cependant, le peuplement de la boîte de liste nécessite un appel de fil croisé, comme expliqué dans les deux articles à balles suivantes.</span><span class="sxs-lookup"><span data-stu-id="95329-117">However, populating the list box requires a cross-thread call, as explained in the next two bulleted items.</span></span>

- <span data-ttu-id="95329-118">`DirectorySearcher`définit la `AddFiles` méthode pour ajouter des fichiers à une boîte de liste; cependant, `RecurseDirectory` ne `AddFiles` peut `AddFiles` pas invoquer directement `DirectorySearcher`parce que peut exécuter seulement dans le fil STA qui a créé .</span><span class="sxs-lookup"><span data-stu-id="95329-118">`DirectorySearcher` defines the `AddFiles` method to add files to a list box; however, `RecurseDirectory` cannot directly invoke `AddFiles` because `AddFiles` can execute only in the STA thread that created `DirectorySearcher`.</span></span>

- <span data-ttu-id="95329-119">La seule `RecurseDirectory` façon `AddFiles` peut appeler est par un appel <xref:System.Windows.Forms.Control.Invoke%2A> de <xref:System.Windows.Forms.Control.BeginInvoke%2A> fil `AddFiles` croisé - `DirectorySearcher`c’est-à-dire, en appelant ou en marshal au fil de création de .</span><span class="sxs-lookup"><span data-stu-id="95329-119">The only way `RecurseDirectory` can call `AddFiles` is through a cross-thread call — that is, by calling <xref:System.Windows.Forms.Control.Invoke%2A> or <xref:System.Windows.Forms.Control.BeginInvoke%2A> to marshal `AddFiles` to the creation thread of `DirectorySearcher`.</span></span> <span data-ttu-id="95329-120">`RecurseDirectory`utilise <xref:System.Windows.Forms.Control.BeginInvoke%2A> de sorte que l’appel peut être fait asynchrone.</span><span class="sxs-lookup"><span data-stu-id="95329-120">`RecurseDirectory` uses <xref:System.Windows.Forms.Control.BeginInvoke%2A> so that the call can be made asynchronously.</span></span>

- <span data-ttu-id="95329-121">Le marshalage d’une méthode nécessite l’équivalent d’un pointeur de fonction ou d’un rappel.</span><span class="sxs-lookup"><span data-stu-id="95329-121">Marshaling a method requires the equivalent of a function pointer or callback.</span></span> <span data-ttu-id="95329-122">Ceci est accompli en utilisant des délégués dans le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="95329-122">This is accomplished using delegates in the .NET Framework.</span></span> <span data-ttu-id="95329-123"><xref:System.Windows.Forms.Control.BeginInvoke%2A>prend un délégué comme argument.</span><span class="sxs-lookup"><span data-stu-id="95329-123"><xref:System.Windows.Forms.Control.BeginInvoke%2A> takes a delegate as an argument.</span></span> <span data-ttu-id="95329-124">`DirectorySearcher`définit donc un`FileListDelegate`délégué ( `AddFiles` ), se `FileListDelegate` lie à un exemple de <xref:System.Windows.Forms.Control.BeginInvoke%2A>dans son constructeur, et passe cette instance déléguée à .</span><span class="sxs-lookup"><span data-stu-id="95329-124">`DirectorySearcher` therefore defines a delegate (`FileListDelegate`), binds `AddFiles` to an instance of `FileListDelegate` in its constructor, and passes this delegate instance to <xref:System.Windows.Forms.Control.BeginInvoke%2A>.</span></span> <span data-ttu-id="95329-125">`DirectorySearcher`définit également un délégué d’événement qui est marshaled lorsque la recherche est terminée.</span><span class="sxs-lookup"><span data-stu-id="95329-125">`DirectorySearcher` also defines an event delegate that is marshaled when the search is completed.</span></span>

```vb
Option Strict
Option Explicit

Imports System.IO
Imports System.Threading
Imports System.Windows.Forms

Namespace Microsoft.Samples.DirectorySearcher
   ' <summary>
   '      This class is a Windows Forms control that implements a simple directory searcher.
   '      You provide, through code, a search string and it will search directories on
   '      a background thread, populating its list box with matches.
   ' </summary>
   Public Class DirectorySearcher
      Inherits Control
      ' Define a special delegate that handles marshaling
      ' lists of file names from the background directory search
      ' thread to the thread that contains the list box.
      Delegate Sub FileListDelegate(files() As String, startIndex As Integer, count As Integer)

      Private _listBox As ListBox
      Private _searchCriteria As String
      Private _searching As Boolean
      Private _deferSearch As Boolean
      Private _searchThread As Thread
      Private _fileListDelegate As FileListDelegate
      Private _onSearchComplete As EventHandler

      Public Sub New()
         _listBox = New ListBox()
         _listBox.Dock = DockStyle.Fill

         Controls.Add(_listBox)

         _fileListDelegate = New FileListDelegate(AddressOf AddFiles)
         _onSearchComplete = New EventHandler(AddressOf OnSearchComplete)
      End Sub

      Public Property SearchCriteria() As String
         Get
            Return _searchCriteria
         End Get
         Set
            ' If currently searching, abort
            ' the search and restart it after
            ' setting the new criteria.
            '
            Dim wasSearching As Boolean = Searching

            If wasSearching Then
               StopSearch()
            End If

            _listBox.Items.Clear()
            _searchCriteria = value

            If wasSearching Then
               BeginSearch()
            End If
         End Set
      End Property

      Public ReadOnly Property Searching() As Boolean
         Get
            Return _searching
         End Get
      End Property

      Public Event SearchComplete As EventHandler

      ' <summary>
      ' This method is called from the background thread.  It is called through
      ' a BeginInvoke call so that it is always marshaled to the thread that
      ' owns the list box control.
      ' </summary>
      ' <param name="files"></param>
      ' <param name="startIndex"></param>
      ' <param name="count"></param>
      Private Sub AddFiles(files() As String, startIndex As Integer, count As Integer)
         While count > 0
            count -= 1
            _listBox.Items.Add(files((startIndex + count)))
         End While
      End Sub

      Public Sub BeginSearch()
         ' Create the search thread, which
         ' will begin the search.
         ' If already searching, do nothing.
         '
         If Searching Then
            Return
         End If

         ' Start the search if the handle has
         ' been created. Otherwise, defer it until the
         ' handle has been created.
         If IsHandleCreated Then
            _searchThread = New Thread(New ThreadStart(AddressOf ThreadProcedure))
            _searching = True
            _searchThread.Start()
         Else
            _deferSearch = True
         End If
      End Sub

      Protected Overrides Sub OnHandleDestroyed(e As EventArgs)
         ' If the handle is being destroyed and you are not
         ' recreating it, then abort the search.
         If Not RecreatingHandle Then
            StopSearch()
         End If
         MyBase.OnHandleDestroyed(e)
      End Sub

      Protected Overrides Sub OnHandleCreated(e As EventArgs)
         MyBase.OnHandleCreated(e)
         If _deferSearch Then
            _deferSearch = False
            BeginSearch()
         End If
      End Sub

      ' <summary>
      ' This method is called by the background thread when it has
      ' finished the search.
      ' </summary>
      ' <param name="sender"></param>
      ' <param name="e"></param>
      Private Sub OnSearchComplete(sender As Object, e As EventArgs)
         RaiseEvent SearchComplete(sender, e)
      End Sub

      Public Sub StopSearch()
         If Not _searching Then
            Return
         End If

         If _searchThread.IsAlive Then
            _searchThread.Abort()
            _searchThread.Join()
         End If

         _searchThread = Nothing
         _searching = False
      End Sub

      ' <summary>
      ' Recurses the given path, adding all files on that path to
      ' the list box. After it finishes with the files, it
      ' calls itself once for each directory on the path.
      ' </summary>
      ' <param name="searchPath"></param>
      Private Sub RecurseDirectory(searchPath As String)
         ' Split searchPath into a directory and a wildcard specification.
         '
         Dim directoryPath As String = Path.GetDirectoryName(searchPath)
         Dim search As String = Path.GetFileName(searchPath)

         ' If a directory or search criteria are not specified, then return.
         '
         If directoryPath Is Nothing Or search Is Nothing Then
            Return
         End If

         Dim files() As String

         ' File systems like NTFS that have
         ' access permissions might result in exceptions
         ' when looking into directories without permission.
         ' Catch those exceptions and return.
         Try
            files = Directory.GetFiles(directoryPath, search)
         Catch e As UnauthorizedAccessException
            Return
         Catch e As DirectoryNotFoundException
            Return
         End Try

         ' Perform a BeginInvoke call to the list box
         ' in order to marshal to the correct thread. It is not
         ' very efficient to perform this marshal once for every
         ' file, so batch up multiple file calls into one
         ' marshal invocation.
         Dim startingIndex As Integer = 0
         While startingIndex < files.Length
            ' Batch up 20 files at once, unless at the
            ' end.
            '
            Dim count As Integer = 20
            If count + startingIndex >= files.Length Then
               count = files.Length - startingIndex
            End If
            ' Begin the cross-thread call. Because you are passing
            ' immutable objects into this invoke method, you do not have to
            ' wait for it to finish. If these were complex objects, you would
            ' have to either create new instances of them or
            ' wait for the thread to process this invoke before modifying
            ' the objects.
            Dim r As IAsyncResult = BeginInvoke(_fileListDelegate, New Object() {files, startingIndex, count})
            startingIndex += count
         End While
         ' Now that you have finished the files in this directory, recurse
         ' for each subdirectory.
         Dim directories As String() = Directory.GetDirectories(directoryPath)
         Dim d As String
         For Each d In  directories
            RecurseDirectory(Path.Combine(d, search))
         Next d
      End Sub

      '/ <summary>
      '/ This is the actual thread procedure. This method runs in a background
      '/ thread to scan directories. When finished, it simply exits.
      '/ </summary>
      Private Sub ThreadProcedure()
         ' Get the search string. Individual
         ' field assigns are atomic in .NET, so you do not
         ' need to use any thread synchronization to grab
         ' the string value here.
         Try
            Dim localSearch As String = SearchCriteria

            ' Now, search the file system.
            '
            RecurseDirectory(localSearch)
         Finally
            ' You are done with the search, so update.
            '
            _searching = False

            ' Raise an event that notifies the user that
            ' the search has terminated.
            ' You do not have to do this through a marshaled call, but
            ' marshaling is recommended for the following reason:
            ' Users of this control do not know that it is
            ' multithreaded, so they expect its events to
            ' come back on the same thread as the control.
            BeginInvoke(_onSearchComplete, New Object() {Me, EventArgs.Empty})
         End Try
      End Sub
   End Class
End Namespace
```

```csharp
namespace Microsoft.Samples.DirectorySearcher
{
   using System;
   using System.IO;
   using System.Threading;
   using System.Windows.Forms;

   /// <summary>
   ///      This class is a Windows Forms control that implements a simple directory searcher.
   ///      You provide, through code, a search string and it will search directories on
   ///      a background thread, populating its list box with matches.
   /// </summary>
   public class DirectorySearcher : Control
   {
      // Define a special delegate that handles marshaling
      // lists of file names from the background directory search
      // thread to the thread that contains the list box.
      private delegate void FileListDelegate(string[] files, int startIndex, int count);

      private ListBox listBox;
      private string  searchCriteria;
      private bool searching;
      private bool deferSearch;
      private Thread searchThread;
      private FileListDelegate fileListDelegate;
      private EventHandler onSearchComplete;

      public DirectorySearcher()
      {
         listBox = new ListBox();
         listBox.Dock = DockStyle.Fill;

         Controls.Add(listBox);

         fileListDelegate = new FileListDelegate(AddFiles);
         onSearchComplete = new EventHandler(OnSearchComplete);
      }

      public string SearchCriteria
      {
         get
         {
            return searchCriteria;
         }
         set
         {
            // If currently searching, abort
            // the search and restart it after
            // setting the new criteria.
            //
            bool wasSearching = Searching;

            if (wasSearching)
            {
               StopSearch();
            }

            listBox.Items.Clear();
            searchCriteria = value;

            if (wasSearching)
            {
               BeginSearch();
            }
         }
      }

      public bool Searching
      {
         get
         {
            return searching;
         }
      }

      public event EventHandler SearchComplete;

      /// <summary>
      /// This method is called from the background thread. It is called through
      /// a BeginInvoke call so that it is always marshaled to the thread that
      /// owns the list box control.
      /// </summary>
      /// <param name="files"></param>
      /// <param name="startIndex"></param>
      /// <param name="count"></param>
      private void AddFiles(string[] files, int startIndex, int count)
      {
         while(count-- > 0)
         {
            listBox.Items.Add(files[startIndex + count]);
         }
      }

      public void BeginSearch()
      {
         // Create the search thread, which
         // will begin the search.
         // If already searching, do nothing.
         //
         if (Searching)
         {
            return;
         }

         // Start the search if the handle has
         // been created. Otherwise, defer it until the
         // handle has been created.
         if (IsHandleCreated)
         {
            searchThread = new Thread(new ThreadStart(ThreadProcedure));
            searching = true;
            searchThread.Start();
         }
         else
         {
            deferSearch = true;
         }
      }

      protected override void OnHandleDestroyed(EventArgs e)
      {
         // If the handle is being destroyed and you are not
         // recreating it, then abort the search.
         if (!RecreatingHandle)
         {
            StopSearch();
         }
         base.OnHandleDestroyed(e);
      }

      protected override void OnHandleCreated(EventArgs e)
      {
         base.OnHandleCreated(e);
         if (deferSearch)
         {
            deferSearch = false;
            BeginSearch();
         }
      }

      /// <summary>
      /// This method is called by the background thread when it has finished
      /// the search.
      /// </summary>
      /// <param name="sender"></param>
      /// <param name="e"></param>
      private void OnSearchComplete(object sender, EventArgs e)
      {
         if (SearchComplete != null)
         {
            SearchComplete(sender, e);
         }
      }

      public void StopSearch()
      {
         if (!searching)
         {
            return;
         }

         if (searchThread.IsAlive)
         {
            searchThread.Abort();
            searchThread.Join();
         }

         searchThread = null;
         searching = false;
      }

      /// <summary>
      /// Recurses the given path, adding all files on that path to
      /// the list box. After it finishes with the files, it
      /// calls itself once for each directory on the path.
      /// </summary>
      /// <param name="searchPath"></param>
      private void RecurseDirectory(string searchPath)
      {
         // Split searchPath into a directory and a wildcard specification.
         //
         string directory = Path.GetDirectoryName(searchPath);
         string search = Path.GetFileName(searchPath);

         // If a directory or search criteria are not specified, then return.
         //
         if (directory == null || search == null)
         {
            return;
         }

         string[] files;

         // File systems like NTFS that have
         // access permissions might result in exceptions
         // when looking into directories without permission.
         // Catch those exceptions and return.
         try
         {
            files = Directory.GetFiles(directory, search);
         }
         catch(UnauthorizedAccessException)
         {
            return;
         }
         catch(DirectoryNotFoundException)
         {
            return;
         }

         // Perform a BeginInvoke call to the list box
         // in order to marshal to the correct thread. It is not
         // very efficient to perform this marshal once for every
         // file, so batch up multiple file calls into one
         // marshal invocation.
         int startingIndex = 0;

         while(startingIndex < files.Length)
         {
            // Batch up 20 files at once, unless at the
            // end.
            //
            int count = 20;
            if (count + startingIndex >= files.Length)
            {
               count = files.Length - startingIndex;
            }

            // Begin the cross-thread call. Because you are passing
            // immutable objects into this invoke method, you do not have to
            // wait for it to finish. If these were complex objects, you would
            // have to either create new instances of them or
            // wait for the thread to process this invoke before modifying
            // the objects.
            IAsyncResult r = BeginInvoke(fileListDelegate, new object[] {files, startingIndex, count});
            startingIndex += count;
         }

         // Now that you have finished the files in this directory, recurse for
         // each subdirectory.
         string[] directories = Directory.GetDirectories(directory);
         foreach(string d in directories)
         {
            RecurseDirectory(Path.Combine(d, search));
         }
      }

      /// <summary>
      /// This is the actual thread procedure. This method runs in a background
      /// thread to scan directories. When finished, it simply exits.
      /// </summary>
      private void ThreadProcedure()
      {
         // Get the search string. Individual
         // field assigns are atomic in .NET, so you do not
         // need to use any thread synchronization to grab
         // the string value here.
         try
         {
            string localSearch = SearchCriteria;

            // Now, search the file system.
            //
            RecurseDirectory(localSearch);
         }
         finally
         {
            // You are done with the search, so update.
            //
            searching = false;

            // Raise an event that notifies the user that
            // the search has terminated.
            // You do not have to do this through a marshaled call, but
            // marshaling is recommended for the following reason:
            // Users of this control do not know that it is
            // multithreaded, so they expect its events to
            // come back on the same thread as the control.
            BeginInvoke(onSearchComplete, new object[] {this, EventArgs.Empty});
         }
      }
   }
}
```

## <a name="using-the-multithreaded-control-on-a-form"></a><span data-ttu-id="95329-126">Utilisation du contrôle multilisible sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="95329-126">Using the Multithreaded Control on a Form</span></span>
 <span data-ttu-id="95329-127">L’exemple suivant montre comment `DirectorySearcher` le contrôle multithlié peut être utilisé sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="95329-127">The following example shows how the multithreaded `DirectorySearcher` control can be used on a form.</span></span>

```vb
Option Explicit
Option Strict

Imports System.Collections
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Windows.Forms
Imports Microsoft.Samples.DirectorySearcher

Namespace SampleUsage

   ' <summary>
   '      Summary description for Form1.
   ' </summary>
   Public Class Form1
      Inherits System.Windows.Forms.Form
      Private WithEvents directorySearcher As DirectorySearcher
      Private searchText As System.Windows.Forms.TextBox
      Private searchLabel As System.Windows.Forms.Label
      Private WithEvents searchButton As System.Windows.Forms.Button

      Public Sub New()
         '
         ' Required for Windows Forms designer support.
         '
         InitializeComponent()
         '
         ' Add any constructor code after InitializeComponent call here.
         '
      End Sub

      #Region "Windows Form Designer generated code"
      ' <summary>
      '      Required method for designer support. Do not modify
      '      the contents of this method with the code editor.
      ' </summary>
      Private Sub InitializeComponent()
         Me.directorySearcher = New Microsoft.Samples.DirectorySearcher.DirectorySearcher()
         Me.searchButton = New System.Windows.Forms.Button()
         Me.searchText = New System.Windows.Forms.TextBox()
         Me.searchLabel = New System.Windows.Forms.Label()
         Me.directorySearcher.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Bottom Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right
         Me.directorySearcher.Location = New System.Drawing.Point(8, 72)
         Me.directorySearcher.SearchCriteria = Nothing
         Me.directorySearcher.Size = New System.Drawing.Size(271, 173)
         Me.directorySearcher.TabIndex = 2
         Me.searchButton.Location = New System.Drawing.Point(8, 16)
         Me.searchButton.Size = New System.Drawing.Size(88, 40)
         Me.searchButton.TabIndex = 0
         Me.searchButton.Text = "&Search"
         Me.searchText.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right
         Me.searchText.Location = New System.Drawing.Point(104, 24)
         Me.searchText.Size = New System.Drawing.Size(175, 20)
         Me.searchText.TabIndex = 1
         Me.searchText.Text = "c:\*.cs"
         Me.searchLabel.ForeColor = System.Drawing.Color.Red
         Me.searchLabel.Location = New System.Drawing.Point(104, 48)
         Me.searchLabel.Size = New System.Drawing.Size(176, 16)
         Me.searchLabel.TabIndex = 3
         Me.ClientSize = New System.Drawing.Size(291, 264)
         Me.Controls.AddRange(New System.Windows.Forms.Control() {Me.searchLabel, Me.directorySearcher, Me.searchText, Me.searchButton})
         Me.Text = "Search Directories"
      End Sub
      #End Region

      ' <summary>
      '    The main entry point for the application.
      ' </summary>
      <STAThread()> _
      Shared Sub Main()
         Application.Run(New Form1())
      End Sub

      Private Sub searchButton_Click(sender As Object, e As System.EventArgs) Handles searchButton.Click
         directorySearcher.SearchCriteria = searchText.Text
         searchLabel.Text = "Searching..."
         directorySearcher.BeginSearch()
      End Sub

      Private Sub directorySearcher_SearchComplete(sender As Object, e As System.EventArgs) Handles directorySearcher.SearchComplete
         searchLabel.Text = String.Empty
      End Sub
   End Class
End Namespace
```

```csharp
namespace SampleUsage
{
   using System;
   using System.Collections;
   using System.ComponentModel;
   using System.Data;
   using System.Drawing;
   using System.Windows.Forms;
   using Microsoft.Samples.DirectorySearcher;

   /// <summary>
   ///      Summary description for Form1.
   /// </summary>
   public class Form1 : System.Windows.Forms.Form
   {
      private DirectorySearcher directorySearcher;
      private System.Windows.Forms.TextBox searchText;
      private System.Windows.Forms.Label searchLabel;
      private System.Windows.Forms.Button searchButton;

      public Form1()
      {
         //
         // Required for Windows Forms designer support.
         //
         InitializeComponent();

         //
         // Add any constructor code after InitializeComponent call here.
         //
      }

      #region Windows Form Designer generated code
      /// <summary>
      ///      Required method for designer support. Do not modify
      ///      the contents of this method with the code editor.
      /// </summary>
      private void InitializeComponent()
      {
         this.directorySearcher = new Microsoft.Samples.DirectorySearcher.DirectorySearcher();
         this.searchButton = new System.Windows.Forms.Button();
         this.searchText = new System.Windows.Forms.TextBox();
         this.searchLabel = new System.Windows.Forms.Label();
         this.directorySearcher.Anchor = (((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Bottom)
            | System.Windows.Forms.AnchorStyles.Left)
            | System.Windows.Forms.AnchorStyles.Right);
         this.directorySearcher.Location = new System.Drawing.Point(8, 72);
         this.directorySearcher.SearchCriteria = null;
         this.directorySearcher.Size = new System.Drawing.Size(271, 173);
         this.directorySearcher.TabIndex = 2;
         this.directorySearcher.SearchComplete += new System.EventHandler(this.directorySearcher_SearchComplete);
         this.searchButton.Location = new System.Drawing.Point(8, 16);
         this.searchButton.Size = new System.Drawing.Size(88, 40);
         this.searchButton.TabIndex = 0;
         this.searchButton.Text = "&Search";
         this.searchButton.Click += new System.EventHandler(this.searchButton_Click);
         this.searchText.Anchor = ((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Left)
            | System.Windows.Forms.AnchorStyles.Right);
         this.searchText.Location = new System.Drawing.Point(104, 24);
         this.searchText.Size = new System.Drawing.Size(175, 20);
         this.searchText.TabIndex = 1;
         this.searchText.Text = "c:\\*.cs";
         this.searchLabel.ForeColor = System.Drawing.Color.Red;
         this.searchLabel.Location = new System.Drawing.Point(104, 48);
         this.searchLabel.Size = new System.Drawing.Size(176, 16);
         this.searchLabel.TabIndex = 3;
         this.ClientSize = new System.Drawing.Size(291, 264);
         this.Controls.AddRange(new System.Windows.Forms.Control[] {this.searchLabel,
                                                        this.directorySearcher,
                                                        this.searchText,
                                                        this.searchButton});
         this.Text = "Search Directories";

      }
      #endregion

      /// <summary>
      ///    The main entry point for the application.
      /// </summary>
      [STAThread]
      static void Main()
      {
         Application.Run(new Form1());
      }

      private void searchButton_Click(object sender, System.EventArgs e)
      {
         directorySearcher.SearchCriteria = searchText.Text;
         searchLabel.Text = "Searching...";
         directorySearcher.BeginSearch();
      }

      private void directorySearcher_SearchComplete(object sender, System.EventArgs e)
      {
         searchLabel.Text = string.Empty;
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="95329-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95329-128">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="95329-129">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95329-129">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="95329-130">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="95329-130">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
