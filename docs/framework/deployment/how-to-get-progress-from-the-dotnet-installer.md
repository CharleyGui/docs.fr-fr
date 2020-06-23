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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Guide pratique pour obtenir la progression à partir du programme d’installation du .NET Framework 4.5

.NET Framework 4.5 est un runtime redistribuable. Si vous développez des applications pour cette version du .NET Framework, vous pouvez inclure (chaîner) le programme d’installation de .NET Framework 4.5 en tant que composant requis du programme d’installation de votre application. Pour présenter une expérience d’installation unifiée ou personnalisée, vous souhaiterez peut-être lancer le programme d’installation de .NET Framework 4.5 en mode silencieux et suivre sa progression tout en affichant la progression de l’installation de votre application. Pour activer le suivi en mode silencieux, le programme d’installation de .NET Framework 4.5 (qui peut être observé) définit un protocole en utilisant un segment d’E/S mappées en mémoire (MMIO) pour communiquer avec votre programme d’installation (l’observateur ou le programme de chaînage). Ce protocole définit un moyen pour un programme de chaînage d’obtenir des informations sur la progression, d’obtenir des résultats détaillés, de répondre aux messages et d’annuler l’installation de .NET Framework 4.5.

- **Appel**. Pour appeler le programme d’installation de .NET Framework 4.5 et recevoir des informations sur la progression à partir de la section MMIO, votre programme d’installation doit effectuer les opérations suivantes :

    1. Appelez le programme redistribuable .NET Framework 4,5 :

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        où *section-name* est le nom que vous souhaitez utiliser pour identifier votre application. Le programme d’installation du .NET Framework lit et écrit dans la section MMIO de façon asynchrone. Vous trouverez donc peut-être utile d’utiliser des événements et des messages pendant cette période. Dans l’exemple, le processus d’installation du .NET Framework est créé par un constructeur qui alloue la section MMIO (`TheSectionName`) et définit un événement (`TheEventName`) :

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Remplacez ces noms par des noms uniques à votre programme d’installation.

    2. Lisez à partir de la section MMIO. Dans le .NET Framework 4,5, les opérations de téléchargement et d’installation sont simultanées : une partie du .NET Framework peut être installée alors qu’une autre partie est en cours de téléchargement. Ainsi, la progression est renvoyée (autrement dit, écrite) dans la section MMIO sous forme de deux nombres (`m_downloadSoFar` et `m_installSoFar`) qui vont de 0 à 255. Quand la valeur 255 est écrite et que le .NET Framework se ferme, l’installation est terminée.

- **Codes de sortie**. Les codes de sortie suivants de la commande d’appel du programme redistribuable de .NET Framework 4.5 indiquent si le programme d’installation a réussi ou échoué :

  - 0 : l’installation s’est terminée correctement.

  - 3010 : l’installation s’est terminée correctement. Un redémarrage système est nécessaire.

  - 1602 : le programme d’installation a été annulé.

  - Tous les autres codes : le programme d’installation a rencontré des erreurs. Pour plus d’informations, examinez les fichiers journaux créés dans %temp%.

- **Annulation de l’installation**. Vous pouvez annuler l’installation à tout moment en utilisant la méthode `Abort` pour définir les indicateurs `m_downloadAbort` et `m_ installAbort` dans la section MMIO.

## <a name="chainer-sample"></a>Exemple de programme de chaînage

L’exemple de programme de chaînage lance et suit de manière silencieuse l’installation de .NET Framework 4.5 tout en affichant la progression. Cet exemple est similaire à l’exemple de programme de chaînage fourni pour le .NET Framework 4. Toutefois, il peut en plus éviter les redémarrages système en traitant la boîte de message pour la fermeture des applications .NET Framework 4. Pour plus d’informations sur cette boîte de message, consultez [Réduction des redémarrages système lors des installations du .NET Framework 4.5](reducing-system-restarts.md). Vous pouvez utiliser cet exemple avec le programme d’installation du .NET Framework 4. Dans ce scénario, le message n’est tout simplement pas envoyé.

> [!WARNING]
> Vous devez exécuter l’exemple en tant qu’administrateur.

Vous pouvez télécharger la solution Visual Studio complète pour l’[exemple de programme de chaînage du .NET Framework 4.5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) à partir de la galerie d’exemples MSDN.

Les sections suivantes décrivent les fichiers importants dans cet exemple : MMIOChainer.h, ChainingdotNet4.cpp et IProgressObserver.h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- Le fichier MMIOChainer.h (voir le [code complet](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contient la définition de la structure de données et la classe de base à partir de laquelle la classe de programme de chaînage doit être dérivée. .NET Framework 4.5 étend la structure de données MMIO pour gérer les données dont a besoin le programme d’installation de .NET Framework 4.5. Les modifications apportées à la structure MMIO sont à compatibilité descendante. Ainsi, un programme de chaînage du .NET Framework 4 peut fonctionner avec le programme d’installation du .NET Framework 4.5 sans nécessiter de recompilation. Toutefois, ce scénario ne prend pas en charge la fonctionnalité de réduction des redémarrages système.

    Un champ de version permet d’identifier les révisions du format de message et de la structure. Le programme d’installation du .NET Framework détermine la version de l’interface de programme de chaînage en appelant la fonction `VirtualQuery` pour déterminer la taille du mappage de fichier. Si la taille est assez élevée pour contenir le champ de version, le programme d’installation du .NET Framework utilise la valeur spécifiée. Si le mappage de fichier est trop petit pour contenir un champ de version, ce qui est le cas avec le .NET Framework 4, le processus d’installation part du principe que la version est 0 (4). Si le programme de chaînage ne prend pas en charge la version du message que le programme d’installation du .NET Framework souhaite envoyer, celui-ci considère que la réponse est « Ignorer ».

    La structure de données MMIO est définie comme suit :

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

- La structure de données `MmioDataStructure` ne doit pas être utilisée directement. Utilisez plutôt la classe `MmioChainer` pour implémenter votre programme de chaînage. Dérivez à partir de la classe `MmioChainer` pour chaîner le redistribuable de .NET Framework 4.5.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- Le fichier IProgressObserver.h implémente un observateur de progression ([voir l’intégralité du code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)). L’observateur est informé de la progression du téléchargement et de l’installation (spécifiée en tant que `char` non signé compris entre 0 et 255, indiquant de 1 % à 100 % terminé). L’observateur est également averti quand l’élément chaîné envoie un message, et l’observateur doit envoyer une réponse.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ChainingdotNet4.5.cpp

- Le fichier [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) implémente la classe `Server`, qui dérive de la classe `MmioChainer` et substitue les méthodes appropriées pour afficher les informations de progression. MmioChainer crée une section avec le nom de section spécifié et initialise le programme de chaînage avec le nom d’événement spécifié. Le nom de l’événement est enregistré dans la structure de données mappée. Vous devez faire en sorte que les noms de section et d’événement soient uniques. La classe `Server` dans le code suivant lance le programme d’installation spécifié, surveille sa progression et retourne un code de sortie.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    L’installation est démarrée dans la méthode Main.

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

- Avant de lancer l’installation, le programme de chaînage vérifie si .NET Framework 4.5 est déjà installé en appelant `IsNetFx4Present` :

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

- Vous pouvez changer le chemin du fichier exécutable (Setup.exe dans l’exemple) dans la méthode `Launch` pour qu’il pointe vers son emplacement correct, ou personnaliser le code afin de déterminer l’emplacement. La classe de base `MmioChainer` fournit une méthode `Run()` bloquante appelée par la classe dérivée.

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

- La méthode `Send` intercepte et traite les messages. Dans cette version du .NET Framework, le seul message pris en charge est le message de fermeture d’application.

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

- Les données de progression sont un `char` non signé compris entre 0 (0 %) et 255 (100 %).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- Le HRESULT est passé à la méthode `Finished`.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > Le redistribuable de .NET Framework 4.5 écrit généralement de nombreux messages de progression et un message unique qui indique l’achèvement (du côté du programme de chaînage). Il lit également de façon asynchrone, à la recherche d’enregistrements `Abort`. S’il reçoit un enregistrement `Abort`, il annule l’installation et écrit un enregistrement terminé avec E_ABORT comme données une fois que l’installation a été annulée et que les opérations d’installation ont été annulées.

Un serveur classique crée un nom de fichier MMIO aléatoire, crée le fichier (comme illustré dans l’exemple de code précédent, `Server::CreateSection`) et lance le redistribuable en utilisant la méthode `CreateProcess` et en passant le nom du canal avec l’option `-pipe someFileSectionName`. Le serveur doit implémenter les méthodes `OnProgress`, `Send` et `Finished` avec du code d’application propre à l’interface utilisateur.

## <a name="see-also"></a>Voir aussi

- [Guide de déploiement pour les développeurs](deployment-guide-for-developers.md)
- [Déploiement](index.md)
