## Google Analytics

### 태그 설치
    // next.js
    // _document.js
    <script async src={`https://www.googletagmanager.com/gtag/js?id=${process.env.GA_TRACKING_ID}`}/>
    <script
        dangerouslySetInnerHTML={{
            __html: `
                 window.dataLayer = window.dataLayer || [];
                function gtag(){window.dataLayer.push(arguments)}
                gtag('js', new Date());

                gtag('config', '${process.env.GA_TRACKING_ID}');
            `
        }}
    />
### 이벤트 전달
    gtag('event', 'eventName', {
        'event_category': 'category',
        'event_label': 'label',
        'value': 'value'
    });