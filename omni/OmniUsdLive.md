# OmniUSDLive.h

### Brief

This file is in charge of updating the information from other users in your scene, this means that the live mode is disigned to share information in real time.

### Live mode
The live mode work in 2 ways, the next table will show the differences between the two modes:

| Enable | Disable |
|--------|---------|
| You will receive updates from other users.                                                    | You will not receive updates from other users.| 
| Saving a layer will send a delta to the server, to merge your changes with others             | Saving a layer will OVERWRITE it on the server.| 
| Saving a layer will return immediately (not block).                                           | Saving a layer will BLOCK until the layer has been saved.| 
| You must call omniUsdLiveProcess (or omniUsdLiveProcessUpTo) to apply remote updates          | omniUsdLiveLock & omniUsdLiveUnlock don't do anything.| 
|     to your scene and to process any responses the server may have sent about delta updates   | This is functionally equivalent to using Omniverse like a filesystem.|     that you have sent (from calling Save).                                                   |
| You may call omniUsdLiveWaitForPendingUpdates to block until the server has acknowledged      |
|     all the updates that you have sent to it.                                                 |
| You may call omniUsdLiveLock to prevent other users from modifying a layer.                   |

**Note: ** Live mode can be set per-layer with a global default.

---

### Exports
This methods defines the mode where the client will be export, it can be with a basic initialization or a customized initialization with an URL and a mode type.
'''
{
    typedef enum
    {
        eOmniUsdLiveModeDefault,
        eOmniUsdLiveModeDisabled,
        eOmniUsdLiveModeEnabled,
    } OmniUsdLiveMode;

    OMNICLIENT_EXPORT(void)
    omniUsdLiveSetDefaultEnabled(bool enabled)
    OMNICLIENT_NOEXCEPT;

    OMNICLIENT_EXPORT(void)
        omniUsdLiveSetModeForUrl(const char* url, OmniUsdLiveMode mode)
        OMNICLIENT_NOEXCEPT;

    OMNICLIENT_EXPORT(bool)
        omniUsdLiveGetDefaultEnabled()
        OMNICLIENT_NOEXCEPT;

    OMNICLIENT_EXPORT(OmniUsdLiveMode)
        omniUsdLiveGetModeForUrl(const char* url)
        OMNICLIENT_NOEXCEPT;
}
'''
