EasyCam2D
=========

lybrary for create a 2d camera 

exemple of instance of easy 2d camera 

new Easy2DCamera(window.canvas,{"focusOn" : Game.players[1],"pointReferenceX" : config.canvasObject.width/2, "pointReferenceY" :config.canvasObject.height/2, "worldX" : 0 , "worldY" : 0},{ "left" : {"min" : 100, "max" : 200},"right" : {"min" : 50, "max" : 1000} , "up" : {"min" : 50, "max" : 300},"down" : {"min" : 50, "max" : 100}, "speed" : 2 });

exemples of draw canvas with easy camera

myClass.prototype.draw = function(Game)
			{
				var camcoord = Game.gestion.camera.getSpaceInfos();
        
				if(this.color.inside!=undefined)
		 			config.context.fillStyle=this.color.inside;
				if(this.color.outside!=undefined)
		 			config.context.strokeStyle=this.color.outside;
        
		 		this.characts.x = this.box2dObj.GetBody().GetPosition().x*Game.gestion.worldScale;
		 		this.characts.y = this.box2dObj.GetBody().GetPosition().y*Game.gestion.worldScale;
		 		this.characts.w = this.box2dObj.m_shape.m_vertices[2].x*Game.gestion.worldScale*2;
		 		this.characts.h = this.box2dObj.m_shape.m_vertices[2].y*Game.gestion.worldScale*2;
		 		this.characts.angle = this.box2dObj.GetBody().GetAngle();
				config.context.beginPath();
				// mise en place de l'angle
				config.context.save();
					//deplacement vers l'objet par rapport à la camera
				config.context.translate((this.characts.x - camcoord.worldX ) , (this.characts.y - camcoord.worldY) );
					//rotate du canvas par L'angle de l'objet unity
				config.context.rotate(this.characts.angle);
		 			//dessins du rectangle
		 		config.context.fillRect(( this.characts.w*0.5)*-1, (this.characts.h*0.5)*-1,this.characts.w,this.characts.h);
					// on restaure le canvas a son etat original.
				config.context.restore();
				// on arrete de dessiner
				config.context.closePath();
			};
