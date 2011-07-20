# Require Java so we can use the Java libraries
require 'java'
require 'lib/htmlunit-2.8.jar'
require 'lib/httpclient-4.0.1.jar'
require 'lib/commons-io-1.4.jar'
require 'lib/commons-logging-1.1.1.jar'
require 'lib/commons-lang-2.4.jar'
require 'lib/commons-codec-1.4.jar'
require 'lib/xml-apis-1.3.04.jar'
require 'lib/commons-collections-3.2.1.jar'
require 'lib/nekohtml-1.9.14.jar'
require 'lib/sac-1.3.jar'
require 'lib/cssparser-0.9.5.jar'
require 'lib/xalan-2.7.1.jar'
require 'lib/xercesImpl-2.9.1.jar'
require 'lib/httpcore-4.0.1.jar'
require 'lib/apache-mime4j-0.6.jar'
require 'lib/httpmime-4.0.1.jar'
require 'lib/htmlunit-core-js-2.8.jar'

require './config'

include_class 'com.gargoylesoftware.htmlunit.WebClient';
include_class 'com.gargoylesoftware.htmlunit.BrowserVersion';

task :default => :update_spreadsheet_of_glory

task :update_spreadsheet_of_glory do
  stats = get_new_pod_stats
  #stats[:pushups]
end

def get_new_pod_stats
  version = BrowserVersion.new( "Netscape", "5.0 (Macintosh; en-US)", "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-US; rv:1.8.1.14) Gecko/20080404 Firefox/2.0.0.14", 5.0)
  client = WebClient.new(version)
  page = client.get_page('https://belugapods.com/login')
  form = page.get_forms.first
  form.get_input_by_name('ident').set_value_attribute USERNAME
  form.get_input_by_name('password').set_value_attribute PASSWORD
  pods_page = form.get_input_by_value("Login").click
  glory_page = pods_page.get_anchor_by_text('Pod of Glory').click
  glory_form = glory_page.get_forms.first
  glory_form.get_text_area_by_name('text').text = 'I am necessary. This is automated.'
  glory_form.get_input_by_value('Send').click
end