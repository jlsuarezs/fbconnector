# FBConnector for Angular2
Easiest way to integrate Facebook Javascript SDK in your Angular2 application.

If you already have Node.js and angular-cli installed:
    ng new <project-name> 
    cd <project-name>

    npm install fbconnector --save
   
Open angular-cli-build.js to include fbconnector:

    /* global require, module */

    var Angular2App = require('angular-cli/lib/broccoli/angular2-app');

    module.exports = function(defaults) {
      return new Angular2App(defaults, {
        vendorNpmFiles: [
          'systemjs/dist/system-polyfills.js',
          'systemjs/dist/system.src.js',
          'zone.js/dist/*.js',
          'es6-shim/es6-shim.js',
          'reflect-metadata/*.js',
          'rxjs/**/*.js',
          '@angular/**/*.js',
          'fbconnector/src/*.js'
        ]
      });
    };

Then build:

    ng build

Open /src/system-config.ts to add:

    /** Map relative paths to URLs. */
	const map: any = {
	  'fbconnector': 'vendor/fbconnector/src'
	};

	/** User packages configuration. */
	const packages: any = {
	  fbconnector: {
	    defaultExtension: 'js',
	    main: 'FBConnector.js'
	  }
	};

And use it:

    import {FBConnector} from 'fbconnector/fbconnector';

...

    ngOnInit() {
        var fbCon: FBConnector = new FBConnector('YOUR-FBAPPID-HERE');
        fbCon.initFB();
    }

...

