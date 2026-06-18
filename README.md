import React, { useState, useEffect } from 'react';
import { Menu, X, Github, Linkedin, Mail, ExternalLink, ChevronDown } from 'lucide-react';

export default function Portfolio() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [isScrolled, setIsScrolled] = useState(false);
  const [activeSection, setActiveSection] = useState('home');

  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const skills = [
    { category: 'Frontend', items: ['HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Responsive Design'] },
    { category: 'Backend', items: ['PHP', 'Laravel', 'MySQL', 'Database Design', 'Authentication'] },
    { category: 'Tools', items: ['Git/GitHub', 'VS Code', 'REST APIs', 'CRUD Operations', 'Problem Solving'] }
  ];

  const projects = [
    {
      title: 'MAUVE - Fashion E-Commerce',
      description: 'A modern e-commerce platform for fashion retail with product management, shopping cart, and secure checkout.',
      tech: ['Laravel', 'PHP','React.js', 'MySQL', 'Bootstrap', 'JavaScript'],
      link: 'https://mauve-store.vercel.app',
      color: 'from-purple-500 to-pink-500'
    },
    {
      title: 'ShopingNow - E-Commerce Web App',
      description: 'Full-featured e-commerce application with user authentication, product filtering, and order management.',
      tech: ['PHP', 'MySQL', 'HTML/CSS', 'JavaScript', 'Bootstrap'],
      link: 'https://shopingnow56.netlify.app',
      color: 'from-blue-500 to-cyan-500'
    },
    {
      title: 'Wellness Clinic - Healthcare Platform',
      description: 'Healthcare management system enabling online appointments, patient records, and clinic administration.',
      tech: ['Laravel', 'PHP', 'MySQL', 'Bootstrap', 'CRUD'],
      link: 'https://clinic-frontend-pi.vercel.app',
      color: 'from-green-500 to-emerald-500'
    }
  ];

  const socialLinks = [
    { icon: Github, label: 'GitHub', url: 'https://github.com/Amanullah236', color: 'hover:text-gray-400' },
    { icon: Linkedin, label: 'LinkedIn', url: 'https://www.linkedin.com/in/amanullah-anjum/', color: 'hover:text-blue-400' },
    { icon: Mail, label: 'Email', url: 'mailto:amanullah310ab@gmail.com', color: 'hover:text-red-400' }
  ];

  const scrollToSection = (section) => {
    setActiveSection(section);
    setIsMenuOpen(false);
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-950 via-slate-900 to-slate-950 text-white overflow-hidden">
      {/* Background decorative elements */}
      <div className="fixed inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-20 right-40 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl animate-pulse"></div>
        <div className="absolute bottom-20 left-40 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl animate-pulse" style={{ animationDelay: '1s' }}></div>
      </div>

      {/* Navigation */}
      <nav className={`fixed w-full top-0 z-50 transition-all duration-300 ${isScrolled ? 'bg-slate-950/95 backdrop-blur-md shadow-lg shadow-blue-500/10' : 'bg-transparent'}`}>
        <div className="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            <div className="flex items-center gap-2">
              <div className="w-10 h-10 rounded-lg bg-gradient-to-br from-blue-400 to-blue-600 flex items-center justify-center font-bold text-lg">
                AA
              </div>
              <span className="text-xl font-bold hidden sm:inline">Amanullah</span>
            </div>

            {/* Desktop Menu */}
            <div className="hidden md:flex gap-8">
              {['Home', 'Projects', 'Skills', 'Contact'].map((item) => (
                <button
                  key={item}
                  onClick={() => scrollToSection(item.toLowerCase())}
                  className={`transition-colors duration-300 font-medium ${activeSection === item.toLowerCase() ? 'text-blue-400' : 'text-gray-300 hover:text-blue-400'}`}
                >
                  {item}
                </button>
              ))}
            </div>

            {/* Mobile Menu Button */}
            <button onClick={() => setIsMenuOpen(!isMenuOpen)} className="md:hidden p-2">
              {isMenuOpen ? <X size={24} /> : <Menu size={24} />}
            </button>
          </div>

          {/* Mobile Menu */}
          {isMenuOpen && (
            <div className="md:hidden pb-4 space-y-2">
              {['Home', 'Projects', 'Skills', 'Contact'].map((item) => (
                <button
                  key={item}
                  onClick={() => scrollToSection(item.toLowerCase())}
                  className="block w-full text-left px-4 py-2 text-gray-300 hover:text-blue-400 hover:bg-blue-400/10 rounded transition-colors"
                >
                  {item}
                </button>
              ))}
            </div>
          )}
        </div>
      </nav>

      {/* Hero Section */}
      <section className="min-h-screen flex items-center justify-center pt-20 px-4 relative z-10">
        <div className="max-w-4xl w-full">
          <div className="grid md:grid-cols-2 gap-8 items-center">
            {/* Left - Content */}
            <div className="space-y-6">
              <div className="inline-block px-4 py-2 bg-blue-500/20 rounded-full border border-blue-400/30">
                <p className="text-blue-300 text-sm font-semibold">Full-Stack Web Developer</p>
              </div>
              
              <h1 className="text-5xl md:text-6xl font-bold leading-tight">
                Hi, I'm <span className="bg-gradient-to-r from-blue-400 to-cyan-400 bg-clip-text text-transparent">Amanullah</span>
              </h1>
              
              <p className="text-xl text-gray-300 leading-relaxed">
                Building scalable, modern web applications with <span className="text-blue-300 font-semibold">PHP, Laravel, MySQL & JavaScript</span>. Currently pursuing my Software Engineering degree while creating real-world projects.
              </p>

              <div className="flex gap-4 pt-4">
                <a href="mailto:amanullah310ab@gmail.com" className="px-8 py-3 bg-gradient-to-r from-blue-500 to-blue-600 rounded-lg font-semibold hover:shadow-lg hover:shadow-blue-500/50 transition-all duration-300 hover:scale-105">
                  Get in Touch
                </a>
                <a href="https://github.com/Amanullah236" target="_blank" rel="noopener noreferrer" className="px-8 py-3 border border-blue-400 rounded-lg font-semibold hover:bg-blue-400/10 transition-all duration-300">
                  View Projects
                </a>
              </div>

              {/* Stats */}
              <div className="grid grid-cols-3 gap-4 pt-8 border-t border-gray-700/50">
                <div>
                  <p className="text-2xl font-bold text-blue-400">50+</p>
                  <p className="text-sm text-gray-400">Projects Built</p>
                </div>
                <div>
                  <p className="text-2xl font-bold text-blue-400">1+</p>
                  <p className="text-sm text-gray-400">Years Experience</p>
                </div>
                <div>
                  <p className="text-2xl font-bold text-blue-400">100%</p>
                  <p className="text-sm text-gray-400">Committed</p>
                </div>
              </div>
            </div>

            {/* Right - Image */}
            <div className="relative">
              <div className="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-purple-500/20 rounded-2xl blur-2xl"></div>
              <div className="relative bg-gradient-to-br from-slate-800 to-slate-900 rounded-2xl p-4 border border-blue-400/20">
                <div className="aspect-square rounded-xl overflow-hidden bg-slate-800">
                  <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 400'%3E%3Crect fill='%231e293b' width='400' height='400'/%3E%3Ctext x='200' y='200' text-anchor='middle' dy='.3em' fill='%2364748b' font-size='18' font-family='system-ui'%3EProfile Photo%3C/text%3E%3C/svg%3E" alt="Profile" className="w-full h-full object-cover" />
                </div>
              </div>
            </div>
          </div>

          {/* Scroll Indicator */}
          <div className="flex justify-center mt-16 animate-bounce">
            <ChevronDown className="text-blue-400" size={32} />
          </div>
        </div>
      </section>

      {/* Projects Section */}
      <section className="py-20 px-4 relative z-10">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold mb-4">Featured Projects</h2>
            <p className="text-xl text-gray-400">Showcasing real-world applications built with modern web technologies</p>
          </div>

          <div className="grid md:grid-cols-3 gap-6">
            {projects.map((project, idx) => (
              <a
                key={idx}
                href={project.link}
                target="_blank"
                rel="noopener noreferrer"
                className="group relative bg-gradient-to-br from-slate-800 to-slate-900 rounded-2xl p-6 border border-gray-700 hover:border-blue-400/50 transition-all duration-300 hover:shadow-lg hover:shadow-blue-500/20 hover:scale-105"
              >
                {/* Gradient Background */}
                <div className={`absolute inset-0 bg-gradient-to-br ${project.color} opacity-0 group-hover:opacity-10 rounded-2xl transition-opacity duration-300`}></div>

                <div className="relative z-10">
                  {/* Tech Stack */}
                  <div className="flex flex-wrap gap-2 mb-4">
                    {project.tech.slice(0, 3).map((tech, i) => (
                      <span key={i} className="text-xs px-2 py-1 bg-blue-500/20 text-blue-300 rounded">
                        {tech}
                      </span>
                    ))}
                  </div>

                  {/* Title & Description */}
                  <h3 className="text-xl font-bold mb-3 group-hover:text-blue-400 transition-colors">{project.title}</h3>
                  <p className="text-gray-400 mb-4 line-clamp-2">{project.description}</p>

                  {/* Link */}
                  <div className="flex items-center text-blue-400 group-hover:text-blue-300 transition-colors">
                    <span className="text-sm font-semibold">View Project</span>
                    <ExternalLink size={16} className="ml-2 group-hover:translate-x-1 transition-transform" />
                  </div>
                </div>
              </a>
            ))}
          </div>
        </div>
      </section>

      {/* Skills Section */}
      <section className="py-20 px-4 relative z-10">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold mb-4">Technical Skills</h2>
            <p className="text-xl text-gray-400">Expertise in full-stack development across frontend and backend</p>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            {skills.map((skillGroup, idx) => (
              <div key={idx} className="relative">
                <div className="absolute inset-0 bg-gradient-to-br from-blue-500/10 to-purple-500/10 rounded-xl blur-xl"></div>
                <div className="relative bg-slate-800/50 backdrop-blur rounded-xl p-8 border border-gray-700">
                  <h3 className="text-2xl font-bold text-blue-400 mb-6">{skillGroup.category}</h3>
                  <ul className="space-y-3">
                    {skillGroup.items.map((skill, i) => (
                      <li key={i} className="flex items-center gap-3 text-gray-300">
                        <span className="w-2 h-2 bg-blue-400 rounded-full"></span>
                        {skill}
                      </li>
                    ))}
                  </ul>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section className="py-20 px-4 relative z-10">
        <div className="max-w-2xl mx-auto text-center">
          <h2 className="text-4xl md:text-5xl font-bold mb-6">Let's Work Together</h2>
          <p className="text-xl text-gray-400 mb-12">
            I'm always interested in hearing about new projects and opportunities. Whether you have a question or just want to chat, feel free to reach out!
          </p>

          {/* Contact Methods */}
          <div className="space-y-4 mb-12">
            <a href="mailto:amanullah310ab@gmail.com" className="block px-8 py-4 bg-gradient-to-r from-blue-500 to-blue-600 rounded-xl font-semibold hover:shadow-lg hover:shadow-blue-500/50 transition-all duration-300 hover:scale-105">
              📧 amanullah310ab@gmail.com
            </a>
            <p className="text-gray-400">📍 Rahim Yar Khan, Punjab, Pakistan</p>
            <p className="text-gray-400">📱 +923498673236</p>
          </div>

          {/* Social Links */}
          <div className="flex justify-center gap-6 mb-12">
            {socialLinks.map((social, idx) => {
              const Icon = social.icon;
              return (
                <a
                  key={idx}
                  href={social.url}
                  target="_blank"
                  rel="noopener noreferrer"
                  className={`p-3 bg-slate-800 border border-gray-700 rounded-lg transition-all duration-300 hover:scale-110 hover:border-blue-400 ${social.color}`}
                  title={social.label}
                >
                  <Icon size={24} />
                </a>
              );
            })}
          </div>

          {/* Social Media Links */}
          <div className="flex justify-center gap-4 flex-wrap">
            <a href="https://facebook.com/amanullah" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-blue-400 text-sm transition-colors">Facebook</a>
            <span className="text-gray-600">•</span>
            <a href="https://www.tiktok.com/@aman.dev1" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-blue-400 text-sm transition-colors">TikTok</a>
            <span className="text-gray-600">•</span>
            <a href="https://youtube.com/@amanullahanjum-236" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-blue-400 text-sm transition-colors">YouTube</a>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="border-t border-gray-800 py-12 px-4 relative z-10">
        <div className="max-w-6xl mx-auto text-center text-gray-400">
          <p>© 2026 Amanullah Anjum. All rights reserved.</p>
          <p className="text-sm mt-2">Full Stack Web Developer | Building modern web applications</p>
        </div>
      </footer>
    </div>
  );
}