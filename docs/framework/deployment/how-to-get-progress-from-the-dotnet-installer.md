---
title: Guide pratique pour obtenir la progression à partir du programme d’installation du .NET Framework 4.5
description: Découvrez comment obtenir la progression à partir du programme d’installation de .NET 4,5. Si vous développez des applications pour cette version .NET, vous pouvez inclure (chaîner) le programme d’installation de .NET 4,5 dans le programme d’installation de votre application.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 501fcaa7636d586ddfff8606768d4639fdc010d7
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904258"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="fecc1-104">Guide pratique pour obtenir la progression à partir du programme d’installation du .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="fecc1-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="fecc1-105">.NET Framework 4.5 est un runtime redistribuable.</span><span class="sxs-lookup"><span data-stu-id="fecc1-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="fecc1-106">Si vous développez des applications pour cette version du .NET Framework, vous pouvez inclure (chaîner) le programme d’installation de .NET Framework 4.5 en tant que composant requis du programme d’installation de votre application.</span><span class="sxs-lookup"><span data-stu-id="fecc1-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="fecc1-107">Pour présenter une expérience d’installation unifiée ou personnalisée, vous souhaiterez peut-être lancer le programme d’installation de .NET Framework 4.5 en mode silencieux et suivre sa progression tout en affichant la progression de l’installation de votre application.</span><span class="sxs-lookup"><span data-stu-id="fecc1-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="fecc1-108">Pour activer le suivi en mode silencieux, le programme d’installation de .NET Framework 4.5 (qui peut être observé) définit un protocole en utilisant un segment d’E/S mappées en mémoire (MMIO) pour communiquer avec votre programme d’installation (l’observateur ou le programme de chaînage).</span><span class="sxs-lookup"><span data-stu-id="fecc1-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="fecc1-109">Ce protocole définit un moyen pour un programme de chaînage d’obtenir des informations sur la progression, d’obtenir des résultats détaillés, de répondre aux messages et d’annuler l’installation de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="fecc1-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="fecc1-110">**Appel**.</span><span class="sxs-lookup"><span data-stu-id="fecc1-110">**Invocation**.</span></span> <span data-ttu-id="fecc1-111">Pour appeler le programme d’installation de .NET Framework 4.5 et recevoir des informations sur la progression à partir de la section MMIO, votre programme d’installation doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fecc1-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="fecc1-112">Appelez le programme redistribuable .NET Framework 4,5 :</span><span class="sxs-lookup"><span data-stu-id="fecc1-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="fecc1-113">où *section-name* est le nom que vous souhaitez utiliser pour identifier votre application.</span><span class="sxs-lookup"><span data-stu-id="fecc1-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="fecc1-114">Le programme d’installation du .NET Framework lit et écrit dans la section MMIO de façon asynchrone. Vous trouverez donc peut-être utile d’utiliser des événements et des messages pendant cette période.</span><span class="sxs-lookup"><span data-stu-id="fecc1-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="fecc1-115">Dans l’exemple, le processus d’installation du .NET Framework est créé par un constructeur qui alloue la section MMIO (`TheSectionName`) et définit un événement (`TheEventName`) :</span><span class="sxs-lookup"><span data-stu-id="fecc1-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="fecc1-116">Remplacez ces noms par des noms uniques à votre programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="fecc1-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="fecc1-117">Lisez à partir de la section MMIO.</span><span class="sxs-lookup"><span data-stu-id="fecc1-117">Read from the MMIO section.</span></span> <span data-ttu-id="fecc1-118">Dans le .NET Framework 4,5, les opérations de téléchargement et d’installation sont simultanées : une partie du .NET Framework peut être installée alors qu’une autre partie est en cours de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="fecc1-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="fecc1-119">Ainsi, la progression est renvoyée (autrement dit, écrite) dans la section MMIO sous forme de deux nombres (`m_downloadSoFar` et `m_installSoFar`) qui vont de 0 à 255.</span><span class="sxs-lookup"><span data-stu-id="fecc1-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="fecc1-120">Quand la valeur 255 est écrite et que le .NET Framework se ferme, l’installation est terminée.</span><span class="sxs-lookup"><span data-stu-id="fecc1-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="fecc1-121">**Codes de sortie**.</span><span class="sxs-lookup"><span data-stu-id="fecc1-121">**Exit codes**.</span></span> <span data-ttu-id="fecc1-122">Les codes de sortie suivants de la commande d’appel du programme redistribuable de .NET Framework 4.5 indiquent si le programme d’installation a réussi ou échoué :</span><span class="sxs-lookup"><span data-stu-id="fecc1-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="fecc1-123">0 : l’installation s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="fecc1-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="fecc1-124">3010 : l’installation s’est terminée correctement. Un redémarrage système est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fecc1-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="fecc1-125">1602 : le programme d’installation a été annulé.</span><span class="sxs-lookup"><span data-stu-id="fecc1-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="fecc1-126">Tous les autres codes : le programme d’installation a rencontré des erreurs. Pour plus d’informations, examinez les fichiers journaux créés dans %temp%.</span><span class="sxs-lookup"><span data-stu-id="fecc1-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="fecc1-127">**Annulation de l’installation**.</span><span class="sxs-lookup"><span data-stu-id="fecc1-127">**Canceling setup**.</span></span> <span data-ttu-id="fecc1-128">Vous pouvez annuler l’installation à tout moment en utilisant la méthode `Abort` pour définir les indicateurs `m_downloadAbort` et `m_ installAbort` dans la section MMIO.</span><span class="sxs-lookup"><span data-stu-id="fecc1-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="fecc1-129">Exemple de programme de chaînage</span><span class="sxs-lookup"><span data-stu-id="fecc1-129">Chainer Sample</span></span>

<span data-ttu-id="fecc1-130">L’exemple de programme de chaînage lance et suit de manière silencieuse l’installation de .NET Framework 4.5 tout en affichant la progression.</span><span class="sxs-lookup"><span data-stu-id="fecc1-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="fecc1-131">Cet exemple est similaire à l’exemple de programme de chaînage fourni pour le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fecc1-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="fecc1-132">Toutefois, il peut en plus éviter les redémarrages système en traitant la boîte de message pour la fermeture des applications .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fecc1-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="fecc1-133">Pour plus d’informations sur cette boîte de message, consultez [Réduction des redémarrages système lors des installations du .NET Framework 4.5](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="fecc1-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="fecc1-134">Vous pouvez utiliser cet exemple avec le programme d’installation du .NET Framework 4. Dans ce scénario, le message n’est tout simplement pas envoyé.</span><span class="sxs-lookup"><span data-stu-id="fecc1-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="fecc1-135">Vous devez exécuter l’exemple en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="fecc1-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="fecc1-136">Vous pouvez télécharger la solution Visual Studio complète pour l’[exemple de programme de chaînage du .NET Framework 4.5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) à partir de la galerie d’exemples MSDN.</span><span class="sxs-lookup"><span data-stu-id="fecc1-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="fecc1-137">Les sections suivantes décrivent les fichiers importants dans cet exemple : MMIOChainer.h, ChainingdotNet4.cpp et IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="fecc1-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="fecc1-138">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="fecc1-138">MMIOChainer.h</span></span>

- <span data-ttu-id="fecc1-139">Le fichier MMIOChainer.h (voir le [code complet](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contient la définition de la structure de données et la classe de base à partir de laquelle la classe de programme de chaînage doit être dérivée.</span><span class="sxs-lookup"><span data-stu-id="fecc1-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="fecc1-140">.NET Framework 4.5 étend la structure de données MMIO pour gérer les données dont a besoin le programme d’installation de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="fecc1-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="fecc1-141">Les modifications apportées à la structure MMIO sont à compatibilité descendante. Ainsi, un programme de chaînage du .NET Framework 4 peut fonctionner avec le programme d’installation du .NET Framework 4.5 sans nécessiter de recompilation.</span><span class="sxs-lookup"><span data-stu-id="fecc1-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="fecc1-142">Toutefois, ce scénario ne prend pas en charge la fonctionnalité de réduction des redémarrages système.</span><span class="sxs-lookup"><span data-stu-id="fecc1-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="fecc1-143">Un champ de version permet d’identifier les révisions du format de message et de la structure.</span><span class="sxs-lookup"><span data-stu-id="fecc1-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="fecc1-144">Le programme d’installation du .NET Framework détermine la version de l’interface de programme de chaînage en appelant la fonction `VirtualQuery` pour déterminer la taille du mappage de fichier.</span><span class="sxs-lookup"><span data-stu-id="fecc1-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="fecc1-145">Si la taille est assez élevée pour contenir le champ de version, le programme d’installation du .NET Framework utilise la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fecc1-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="fecc1-146">Si le mappage de fichier est trop petit pour contenir un champ de version, ce qui est le cas avec le .NET Framework 4, le processus d’installation part du principe que la version est 0 (4).</span><span class="sxs-lookup"><span data-stu-id="fecc1-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="fecc1-147">Si le programme de chaînage ne prend pas en charge la version du message que le programme d’installation du .NET Framework souhaite envoyer, celui-ci considère que la réponse est « Ignorer ».</span><span class="sxs-lookup"><span data-stu-id="fecc1-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="fecc1-148">La structure de données MMIO est définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="fecc1-148">The MMIO data structure is defined as follows:</span></span>

    ```cpp
    // MMIO data structure for interprocess communication
        struct MmioDataStructure
        {
            bool m_downloadFinished;               // Is download complete?
            bool m_installFinished;                // Is installation complete?
            bool m_downloadAbort;                  // Set to cause downloader to abort.
            bool m_installAbort;                   // Set to cause installer to abort.
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.
            HRESULT m_hrInternalError;
            WCHAR m_szCurrentItemStep[MAX_PATH];
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.

            BYTE m_version;                        // Version of the data structure, set by chainer:
                                                   // 0x0: .NET Framework 4
                                                   // 0x1: .NET Framework 4.5

            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.
        };
    ```

- <span data-ttu-id="fecc1-149">La structure de données `MmioDataStructure` ne doit pas être utilisée directement. Utilisez plutôt la classe `MmioChainer` pour implémenter votre programme de chaînage.</span><span class="sxs-lookup"><span data-stu-id="fecc1-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="fecc1-150">Dérivez à partir de la classe `MmioChainer` pour chaîner le redistribuable de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="fecc1-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="fecc1-151">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="fecc1-151">IProgressObserver.h</span></span>

- <span data-ttu-id="fecc1-152">Le fichier IProgressObserver.h implémente un observateur de progression ([voir l’intégralité du code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span><span class="sxs-lookup"><span data-stu-id="fecc1-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="fecc1-153">L’observateur est informé de la progression du téléchargement et de l’installation (spécifiée en tant que `char` non signé compris entre 0 et 255, indiquant de 1 % à 100 % terminé).</span><span class="sxs-lookup"><span data-stu-id="fecc1-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="fecc1-154">L’observateur est également averti quand l’élément chaîné envoie un message, et l’observateur doit envoyer une réponse.</span><span class="sxs-lookup"><span data-stu-id="fecc1-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="fecc1-155">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="fecc1-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="fecc1-156">Le fichier [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) implémente la classe `Server`, qui dérive de la classe `MmioChainer` et substitue les méthodes appropriées pour afficher les informations de progression.</span><span class="sxs-lookup"><span data-stu-id="fecc1-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="fecc1-157">MmioChainer crée une section avec le nom de section spécifié et initialise le programme de chaînage avec le nom d’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="fecc1-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="fecc1-158">Le nom de l’événement est enregistré dans la structure de données mappée.</span><span class="sxs-lookup"><span data-stu-id="fecc1-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="fecc1-159">Vous devez faire en sorte que les noms de section et d’événement soient uniques.</span><span class="sxs-lookup"><span data-stu-id="fecc1-159">You should make the section and event names unique.</span></span> <span data-ttu-id="fecc1-160">La classe `Server` dans le code suivant lance le programme d’installation spécifié, surveille sa progression et retourne un code de sortie.</span><span class="sxs-lookup"><span data-stu-id="fecc1-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="fecc1-161">L’installation est démarrée dans la méthode Main.</span><span class="sxs-lookup"><span data-stu-id="fecc1-161">The installation is started in the Main method.</span></span>

    ```cpp
    // Main entry point for program
    int __cdecl main(int argc, _In_count_(argc) char **_argv)
    {
        int result = 0;
        CString args;
        if (argc > 1)
        {
            args = CString(_argv[1]);
        }

        if (IsNetFx4Present(NETFX45_RC_REVISION))
        {
            printf(".NET Framework 4.5 is already installed");
        }
        else
        {
            result = Server().Launch(args);
        }

        return result;
    }
    ```

- <span data-ttu-id="fecc1-162">Avant de lancer l’installation, le programme de chaînage vérifie si .NET Framework 4.5 est déjà installé en appelant `IsNetFx4Present` :</span><span class="sxs-lookup"><span data-stu-id="fecc1-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- <span data-ttu-id="fecc1-163">Vous pouvez changer le chemin du fichier exécutable (Setup.exe dans l’exemple) dans la méthode `Launch` pour qu’il pointe vers son emplacement correct, ou personnaliser le code afin de déterminer l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="fecc1-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="fecc1-164">La classe de base `MmioChainer` fournit une méthode `Run()` bloquante appelée par la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="fecc1-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- <span data-ttu-id="fecc1-165">La méthode `Send` intercepte et traite les messages.</span><span class="sxs-lookup"><span data-stu-id="fecc1-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="fecc1-166">Dans cette version du .NET Framework, le seul message pris en charge est le message de fermeture d’application.</span><span class="sxs-lookup"><span data-stu-id="fecc1-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- <span data-ttu-id="fecc1-167">Les données de progression sont un `char` non signé compris entre 0 (0 %) et 255 (100 %).</span><span class="sxs-lookup"><span data-stu-id="fecc1-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="fecc1-168">Le HRESULT est passé à la méthode `Finished`.</span><span class="sxs-lookup"><span data-stu-id="fecc1-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="fecc1-169">Le redistribuable de .NET Framework 4.5 écrit généralement de nombreux messages de progression et un message unique qui indique l’achèvement (du côté du programme de chaînage).</span><span class="sxs-lookup"><span data-stu-id="fecc1-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="fecc1-170">Il lit également de façon asynchrone, à la recherche d’enregistrements `Abort`.</span><span class="sxs-lookup"><span data-stu-id="fecc1-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="fecc1-171">S’il reçoit un enregistrement `Abort`, il annule l’installation et écrit un enregistrement terminé avec E_ABORT comme données une fois que l’installation a été annulée et que les opérations d’installation ont été annulées.</span><span class="sxs-lookup"><span data-stu-id="fecc1-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="fecc1-172">Un serveur classique crée un nom de fichier MMIO aléatoire, crée le fichier (comme illustré dans l’exemple de code précédent, `Server::CreateSection`) et lance le redistribuable en utilisant la méthode `CreateProcess` et en passant le nom du canal avec l’option `-pipe someFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="fecc1-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="fecc1-173">Le serveur doit implémenter les méthodes `OnProgress`, `Send` et `Finished` avec du code d’application propre à l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fecc1-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="fecc1-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fecc1-174">See also</span></span>

- [<span data-ttu-id="fecc1-175">Guide de déploiement pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="fecc1-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="fecc1-176">Déploiement</span><span class="sxs-lookup"><span data-stu-id="fecc1-176">Deployment</span></span>](index.md)
