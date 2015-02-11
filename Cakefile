fs          = require 'fs'
browserify  = require 'browserify'
coffeeify   = require 'coffeeify'

bundler = ->
  bundler = new browserify debug: yes
  bundler.add './coffee/main.coffee'
  bundler.transform coffeeify
  # bundler.plugin 'minifyify'
  bundler

build = ->  
  bundler().bundle (err, src) ->
    unless err
      fs.writeFile "js/main.js", src, (err) ->
        unless err
          console.log "✔ browserify complete"
        else
          console.error "browserify failed: " + err
    else
      console.error "failed " + err

task 'build', 'Build js/ from coffee/', ->
  build()
