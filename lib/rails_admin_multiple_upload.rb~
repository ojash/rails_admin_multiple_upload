require "rails_admin_multiple_upload/engine"

module RailsAdminMultipleUpload
end

require 'rails_admin/config/actions'

module RailsAdmin
  module Config
    module Actions
      class MultipleUpload < Base
        RailsAdmin::Config::Actions.register(self)
        
        #register_instance_option :object_level do
        #  true
        #end
register_instance_option :member do
    true
  end

  register_instance_option :link_icon do
    'icon-upload'
  end

  register_instance_option :http_methods do
    [:get, :post, :patch]
  end

  register_instance_option :controller do
    Proc.new do
      @response = {}

      if request.patch?
        @place = Place.find(params[:id])
        params[:place][:notes_attributes].each do |photo|
		@place.notes.create!(image: photo[:image], media_type: 'image', user_id: 1 )	
	end
      end

      render :action => @action.template_name
    end
  end
      end
    end
  end
end

