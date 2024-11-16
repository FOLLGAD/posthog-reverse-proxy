# PostHog Reverse Proxy

A fast, free reverse proxy using Netlify redirects.

## Why?

Many browsers and ad blockers prevent analytics scripts from loading when they're served from known analytics domains.

By using a reverse proxy, you can serve PostHog's tracking script from your own domain, significantly reducing blocking while maintaining transparency about your analytics practices.

For best results, use your own domain with a CNAME to your Netlify deployment.

## Setup

### 1. Prerequisites

- A PostHog account and project
- A Netlify account
- Basic knowledge of your PostHog instance URL and project API key

### 2. Quick Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/follgad/posthog-reverse-proxy)

## Usage

### Basic Implementation

Replace your standard PostHog snippet with this modified version:

```javascript
<script>
    !function(t,e){var o,n,p,r;e.__SV||(window.posthog=e,e._i=[],e.init=function(i,s,a){function g(t,e){var o=e.split(".");2==o.length&&(t=t[o[0]],e=o[1]),t[e]=function(){t.push([e].concat(Array.prototype.slice.call(arguments,0)))}}(p=t.createElement("script")).type="text/javascript",p.crossOrigin="anonymous",p.async=!0,p.src=s.api_host.replace(".i.posthog.com","-assets.i.posthog.com")+"/static/array.js",(r=t.getElementsByTagName("script")[0]).parentNode.insertBefore(p,r);var u=e;for(void 0!==a?u=e[a]=[]:a="posthog",u.people=u.people||[],u.toString=function(t){var e="posthog";return"posthog"!==a&&(e+="."+a),t||(e+=" (stub)"),e},u.people.toString=function(){return u.toString(1)+".people (stub)"},o="init capture register register_once register_for_session unregister unregister_for_session getFeatureFlag getFeatureFlagPayload isFeatureEnabled reloadFeatureFlags updateEarlyAccessFeatureEnrollment getEarlyAccessFeatures on onFeatureFlags onSessionId getSurveys getActiveMatchingSurveys renderSurvey canRenderSurvey getNextSurveyStep identify setPersonProperties group resetGroups setPersonPropertiesForFlags resetPersonPropertiesForFlags setGroupPropertiesForFlags resetGroupPropertiesForFlags reset get_distinct_id getGroups get_session_id get_session_replay_url alias set_config startSessionRecording stopSessionRecording sessionRecordingStarted captureException loadToolbar get_property getSessionProperty createPersonProfile opt_in_capturing opt_out_capturing has_opted_in_capturing has_opted_out_capturing clear_opt_in_out_capturing debug".split(" "),n=0;n<o.length;n++)g(u,o[n]);e._i.push([i,s,a])},e.__SV=1)}(document,window.posthog||[]);

    posthog.init('phc_HVZKJWBQsRNDxtuUrLetq6d3k0cP7wGxHGcUiAJqvsE', {
      api_host: "YOUR_DOMAIN_HERE",
      person_profiles: 'identified_only'
    })
</script>
```

Replace `YOUR_DOMAIN_HERE` with your Netlify deployment URL (e.g., `https://your-proxy.netlify.app`).

## License

The Unlicense - see [LICENSE](LICENSE) for details.
