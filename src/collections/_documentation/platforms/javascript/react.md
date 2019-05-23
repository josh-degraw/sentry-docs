---
title: React
sidebar_order: 30
---
<!-- WIZARD -->
To use Sentry with your React application, you will need to use Sentry’s browser JavaScript SDK: `@sentry/browser`.

```bash
# Using yarn
$ yarn add @sentry/browser

# Using npm
$ npm install @sentry/browser
```

On its own, `@sentry/browser` will report any uncaught exceptions triggered by your application.

Initialize Sentry before your application renders

```jsx
import React from 'react';
import * as Sentry from '@sentry/browser';

import MyApp from 'src/app';

Sentry.init({dsn: "___PUBLIC_DSN___"});

ReactDOM.render(<MyApp />, document.getElementById('root'));
```
#### React Error Boundaries

If you’re using React 16 or above, Error Boundaries are an important tool for defining the behavior of your application in the face of errors. Be sure to send errors they catch to Sentry using `Sentry.captureException`. This is also a great opportunity to collect user feedback by using `Sentry.showReportDialog`.

{% capture __alert_content -%}
One important thing to note about the behavior of error boundaries in development mode is that React will rethrow errors they catch. This will result in errors being reported twice to Sentry with the above setup, but this won’t occur in your production build.
{%- endcapture -%}
{%- include components/alert.html
  title="Note"
  content=__alert_content
  level="info"
%}

```jsx
import React from 'react';
import * as Sentry from '@sentry/browser';

class ExampleBoundary extends Component {
    constructor(props) {
        super(props);
        this.state = { error: null, eventId: null };
    }

    componentDidCatch(error, errorInfo) {
      this.setState({ error });
      Sentry.withScope(scope => {
          scope.setExtras(errorInfo);
          const eventId = Sentry.captureException(error);
          this.setState({eventId})
      });
    }

    render() {
        if (this.state.error) {
            //render fallback UI
            return (
              <a onClick={() => Sentry.showReportDialog({ eventId: this.state.eventId })}>Report feedback</a>
            );
        }

        //when there's not an error, render children untouched
        return this.props.children;
    }
}
```

#### Verifying your Installation

You can trigger your first event from your development environment by raising
an exception somewhere within your application. A simple example of this would
be rendering a button like so:

```jsx
return <button onClick={methodDoesNotExist}>Break the world</button>;
```
<!-- ENDWIZARD -->
