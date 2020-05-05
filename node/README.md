# Webpack

webpack  একটা node module  , যা node server end এর কোড (অনেক file ও থাকতে পারে, image, css, jss) bowser এ চলার জন্য  compile করে একটা ফাইল তৈরি করে দেয়। 

#### Rule 
১। globally webpack-cli install করতে হবে ।

২। locally webpack টা আমার পিসি তে install করে নিতে হবে । 

৩। webpack js file এর নাম দিয়ে compile করে নিতে হবে । 


# 4. webpack loader এর মাধ্যমে node module এর কোড compile করা যায় নিচের configuration মাধ্যমে । 
# webpack loader with babel
```composer log
module.exports = {
    entry : "./index.js",
    output: {
        path : __dirname,
        filename : 'dist/output.js'
    },

    module: {
        rules: [
            {
                test: /\.m?js$/,
                exclude: /(node_modules|bower_components)/,
                use: {
                    loader: 'babel-loader',
                    options: {
                        presets: ['@babel/preset-env'],
                        plugins: ['@babel/plugin-proposal-object-rest-spread']
                    }
                }
            }
        ]
    }
}
```