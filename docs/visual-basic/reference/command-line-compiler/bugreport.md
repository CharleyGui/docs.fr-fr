---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793547"
---
# <a name="-bugreport"></a><span data-ttu-id="431db-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="431db-102">-bugreport</span></span>

<span data-ttu-id="431db-103">Crée un fichier que vous pouvez utiliser lorsque vous consignez un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="431db-103">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="431db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431db-104">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="431db-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="431db-105">Arguments</span></span>

|<span data-ttu-id="431db-106">Terme</span><span class="sxs-lookup"><span data-stu-id="431db-106">Term</span></span>|<span data-ttu-id="431db-107">Définition</span><span class="sxs-lookup"><span data-stu-id="431db-107">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="431db-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="431db-108">Required.</span></span> <span data-ttu-id="431db-109">Nom du fichier qui doit contenir votre rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="431db-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="431db-110">Placez le nom de fichier entre guillemets ("") si le nom contient un espace.</span><span class="sxs-lookup"><span data-stu-id="431db-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="431db-111">Notes</span><span class="sxs-lookup"><span data-stu-id="431db-111">Remarks</span></span>

<span data-ttu-id="431db-112">Les informations suivantes sont ajoutées à `file`:</span><span class="sxs-lookup"><span data-stu-id="431db-112">The following information is added to `file`:</span></span>

- <span data-ttu-id="431db-113">Copie de tous les fichiers de code source dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="431db-113">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="431db-114">Liste des options du compilateur utilisées dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="431db-114">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="431db-115">Informations de version sur le compilateur, le common language runtime et le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="431db-115">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="431db-116">Les résultats de la compilation, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="431db-116">Compiler output, if any.</span></span>

- <span data-ttu-id="431db-117">Description du problème auquel vous êtes invité.</span><span class="sxs-lookup"><span data-stu-id="431db-117">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="431db-118">Une description de la façon dont vous pensez que le problème doit être résolu, pour laquelle vous êtes invité à le faire.</span><span class="sxs-lookup"><span data-stu-id="431db-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="431db-119">Étant donné qu’une copie de tous les fichiers de code source est incluse dans `file`, vous souhaiterez peut-être reproduire l’erreur de code (suspect) dans le programme le plus bref possible.</span><span class="sxs-lookup"><span data-stu-id="431db-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="431db-120">L’option `-bugreport` produit un fichier qui contient des informations potentiellement sensibles.</span><span class="sxs-lookup"><span data-stu-id="431db-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="431db-121">Cela comprend l’heure actuelle, la version du compilateur, la version .NET Framework, la version du système d’exploitation, le nom d’utilisateur, les arguments de ligne de commande avec lesquels le compilateur a été exécuté, tout le code source et la forme binaire de tout assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="431db-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="431db-122">Cette option est accessible en spécifiant des options de ligne de commande dans le fichier Web. config pour une compilation côté serveur d’une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="431db-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="431db-123">Pour éviter cela, modifiez le fichier machine. config pour empêcher les utilisateurs de compiler sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="431db-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="431db-124">Si cette option est utilisée avec `-errorreport:prompt`, `-errorreport:queue`ou `-errorreport:send`, et que votre application rencontre une erreur interne du compilateur, les informations contenues dans `file` sont envoyées à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="431db-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="431db-125">Ces informations permettront aux ingénieurs Microsoft d’identifier la cause de l’erreur et peuvent contribuer à améliorer la prochaine version de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="431db-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="431db-126">Par défaut, aucune information n’est envoyée à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="431db-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="431db-127">Toutefois, lorsque vous compilez une application à l’aide de `-errorreport:queue`, qui est activée par défaut, l’application collecte ses rapports d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="431db-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="431db-128">Ensuite, lorsque l’administrateur de l’ordinateur se connecte, le système de création de rapports d’erreurs affiche une fenêtre indépendante qui permet à l’administrateur de transmettre à Microsoft tous les rapports d’erreurs qui se sont produits depuis l’ouverture de session.</span><span class="sxs-lookup"><span data-stu-id="431db-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="431db-129">L’option `-bugreport` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lorsque vous compilez à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="431db-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="431db-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="431db-130">Example</span></span>

<span data-ttu-id="431db-131">L’exemple suivant compile *T2. vb* et place toutes les informations relatives aux rapports de bogues dans le fichier *problem. txt*.</span><span class="sxs-lookup"><span data-stu-id="431db-131">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="431db-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="431db-132">See also</span></span>

- [<span data-ttu-id="431db-133">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="431db-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="431db-134">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="431db-134">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="431db-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="431db-135">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="431db-136">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="431db-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="431db-137">[trustLevel, élément de securityPolicy (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="431db-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
