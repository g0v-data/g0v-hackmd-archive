```javascript=
function useMicroblinkGetImage() {
    const manualCapturePromiseRef = useRef();
 
    const captureLaunch = () => {
        // 1. start microblink video recognize
        //  1-1. get video frame, and ..... (how and what todo?)
        // 2. stop video recognition when the user manually takes a photo
        //  2-1. get image frame, and ..... (how and what todo? call capturePhoto from useCapturePhoto?)
        // 3. how to complete the subsequent process, back to CertificateV2...
    }

    useSubscribe('MICROBLINK_CAPTURE_LAUNCH', captureLaunch)
    useSubscribe('MICROBLINK_CAPTURE_SUCCESS', () => manualCapturePromiseRef.current.resolve())
    useSubscribe('MICROBLINK_CAPTURE_ERROR', () => manualCapturePromiseRef.current.reject())
 
    const handleMicroblinkGetImage = () => {
        dispatch.app.updateSubflow('microblink-ui')
    }
 
    return { handleMicroblinkGetImage }
}
 
function MicroblinkUI() {
    const publishCaptureLaunch = usePublish('MICROBLINK_CAPTURE_LAUNCH')
    const publishCaptureSuccess = usePublish('MICROBLINK_CAPTURE_SUCCESS')
    const publishCaptureError = usePublish('MICROBLINK_CAPTURE_ERROR')
 
    const takePhoto = () => {
        const src = getScreenshot()

        if (src) {
            publishCaptureSuccess(src)
        }
        else {
            publishCaptureError()
        }
    }
 
    return <>
        <Webcam
            // {...some props}
            onWebcamReady={publishCaptureLaunch}
        />
        <UI />
    </>
}
```