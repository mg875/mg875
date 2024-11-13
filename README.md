import React, { useState } from 'react';
import { Card, CardHeader, CardTitle, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Textarea } from '@/components/ui/textarea';
import { UserCircle, BookOpen, Lightbulb, X } from 'lucide-react';

const StartupMeet = () => {
  const [showInvestorForm, setShowInvestorForm] = useState(false);
  const [showPolicies, setShowPolicies] = useState(false);
  const [showIdeaForm, setShowIdeaForm] = useState(false);

  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
    confirmPassword: '',
  });

  const handleSubmit = (e) => {
    e.preventDefault();
    // Aquí iría la lógica de registro
    console.log('Formulario enviado:', formData);
    setShowInvestorForm(false);
  };

  return (
    <div className="min-h-screen bg-gray-100 p-4">
      {/* Header */}
      <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
        <h1 className="text-3xl font-bold text-center text-blue-600 mb-2">Startups Meet</h1>
        <p className="text-gray-600 text-center max-w-3xl mx-auto">
          Una plataforma integral para conectar startups con inversores y mentores, 
          acceder a políticas gubernamentales y compartir ideas innovadoras.
        </p>
      </div>

      {/* Botones principales */}
      <div className="flex flex-wrap gap-4 justify-center mb-6">
        <Button 
          className="flex items-center gap-2 bg-blue-500 hover:bg-blue-600"
          onClick={() => setShowInvestorForm(true)}
        >
          <UserCircle size={20} />
          Perfil de Inversor
        </Button>
        
        <Button 
          className="flex items-center gap-2 bg-green-500 hover:bg-green-600"
          onClick={() => setShowPolicies(true)}
        >
          <BookOpen size={20} />
          Políticas Gubernamentales
        </Button>
        
        <Button 
          className="flex items-center gap-2 bg-purple-500 hover:bg-purple-600"
          onClick={() => setShowIdeaForm(true)}
        >
          <Lightbulb size={20} />
          Subir Ideas
        </Button>
      </div>

      {/* Formulario de Registro de Inversor */}
      {showInvestorForm && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
          <Card className="w-full max-w-md">
            <CardHeader>
              <CardTitle className="flex justify-between items-center">
                Registro de Inversor
                <Button 
                  variant="ghost" 
                  size="icon"
                  onClick={() => setShowInvestorForm(false)}
                >
                  <X size={20} />
                </Button>
              </CardTitle>
            </CardHeader>
            <CardContent>
              <form onSubmit={handleSubmit} className="space-y-4">
                <div>
                  <Input
                    placeholder="Nombre completo"
                    value={formData.name}
                    onChange={(e) => setFormData({...formData, name: e.target.value})}
                    className="w-full"
                  />
                </div>
                <div>
                  <Input
                    type="email"
                    placeholder="Correo electrónico"
                    value={formData.email}
                    onChange={(e) => setFormData({...formData, email: e.target.value})}
                    className="w-full"
                  />
                </div>
                <div>
                  <Input
                    type="password"
                    placeholder="Contraseña"
                    value={formData.password}
                    onChange={(e) => setFormData({...formData, password: e.target.value})}
                    className="w-full"
                  />
                </div>
                <div>
                  <Input
                    type="password"
                    placeholder="Confirmar contraseña"
                    value={formData.confirmPassword}
                    onChange={(e) => setFormData({...formData, confirmPassword: e.target.value})}
                    className="w-full"
                  />
                </div>
                <Button type="submit" className="w-full bg-blue-500 hover:bg-blue-600">
                  Registrarse
                </Button>
              </form>
            </CardContent>
          </Card>
        </div>
      )}

      {/* Modal de Políticas */}
      {showPolicies && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
          <Card className="w-full max-w-2xl">
            <CardHeader>
              <CardTitle className="flex justify-between items-center">
                Políticas Gubernamentales
                <Button 
                  variant="ghost" 
                  size="icon"
                  onClick={() => setShowPolicies(false)}
                >
                  <X size={20} />
                </Button>
              </CardTitle>
            </CardHeader>
            <CardContent className="max-h-[70vh] overflow-y-auto">
              <div className="space-y-4">
                <h3 className="font-semibold">Políticas y Préstamos Disponibles</h3>
                <div className="space-y-2">
                  <p className="text-sm text-gray-600">
                    • Programa de Apoyo a Startups Tecnológicas
                  </p>
                  <p className="text-sm text-gray-600">
                    • Financiamiento para Emprendimientos Sostenibles
                  </p>
                  <p className="text-sm text-gray-600">
                    • Incentivos Fiscales para Nuevas Empresas
                  </p>
                </div>
              </div>
            </CardContent>
          </Card>
        </div>
      )}

      {/* Formulario para Subir Ideas */}
      {showIdeaForm && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
          <Card className="w-full max-w-2xl">
            <CardHeader>
              <CardTitle className="flex justify-between items-center">
                Subir Nueva Idea
                <Button 
                  variant="ghost" 
                  size="icon"
                  onClick={() => setShowIdeaForm(false)}
                >
                  <X size={20} />
                </Button>
              </CardTitle>
            </CardHeader>
            <CardContent>
              <form className="space-y-4">
                <Input
                  placeholder="Título de la idea"
                  className="w-full"
                />
                <Textarea
                  placeholder="Describe tu idea en detalle..."
                  className="w-full min-h-[150px]"
                />
                <div className="flex justify-end">
                  <Button 
                    className="bg-purple-500 hover:bg-purple-600"
                    onClick={() => setShowIdeaForm(false)}
                  >
                    Enviar Idea
                  </Button>
                </div>
              </form>
            </CardContent>
          </Card>
        </div>
      )}

      {/* Contenido Principal */}
      <Card className="max-w-4xl mx-auto">
        <CardHeader>
          <CardTitle>Contenido Principal</CardTitle>
        </CardHeader>
        <CardContent>
          <div className="space-y-4">
            <p className="text-gray-600">
              Startup meet es una plataforma para que las personas se acerquen de forma privada 
              a empresas o inversores ángeles con sus ideas implementadas en diferentes niveles 
              para obtener financiamiento y mentoría.
            </p>
            <p className="text-gray-600">
              Las políticas y pautas para las startups varían de estado a estado. Además, 
              las startups relacionadas con un dominio particular se enfatizan en áreas particulares.
            </p>
            <p className="text-gray-600">
              Los mentores también pueden brindar mentoría. Los préstamos y políticas gubernamentales 
              se pueden ver y también se pueden solicitar a través del portal.
            </p>
          </div>
        </CardContent>
      </Card>
    </div>
  );
};

export default StartupMeet;
