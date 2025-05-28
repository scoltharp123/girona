<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Discover a luxurious 5-night bikepacking adventure through Girona's iconic landscapes. Book your premium cycling experience today.">
    <title>Girona Luxe Bikepacking Escape</title>
    <script src="https://cdn.jsdelivr.net/npm/react@18.3.1/umd/react.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/react-dom@18.3.1/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@babel/standalone@7.25.6/babel.min.js"></script>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fadeIn {
            animation: fadeIn 1s ease-out;
        }
        .hover-scale:hover {
            transform: scale(1.05);
            transition: transform 0.3s ease;
        }
        .route-image {
            max-height: 300px;
            object-fit: cover;
            width: 100%;
            border-radius: 0.75rem;
        }
        .carousel-container {
            position: relative;
            overflow: hidden;
        }
        .carousel {
            display: flex;
            transition: transform 0.5s ease;
        }
        .carousel img {
            flex: 0 0 100%;
        }
    </style>
</head>
<body className="bg-gray-900 text-gray-100 font-sans">
    <div id="root"></div>
    <script type="text/babel">
        const Header = () => (
            <header className="bg-gradient-to-r from-emerald-800 to-teal-900 text-white py-12">
                <div className="container mx-auto text-center animate-fadeIn">
                    <h1 className="text-5xl font-extrabold tracking-tight">Girona Luxe Bikepacking Escape</h1>
                    <p className="mt-4 text-xl font-light italic">A 5-Night Premium Cycling Odyssey Through Catalonia’s Finest Landscapes</p>
                    <a
                        href="#itinerary"
                        className="mt-6 inline-block bg-amber-500 text-gray-900 font-semibold py-3 px-6 rounded-full hover:bg-amber-400 transition hover-scale"
                    >
                        Explore the Journey
                    </a>
                </div>
            </header>
        );

        const ItineraryDay = ({ day, title, distance, elevation, description, accommodation, dining, images }) => {
            const [currentImage, setCurrentImage] = React.useState(0);

            const nextImage = () => {
                setCurrentImage((prev) => (prev + 1) % images.length);
            };

            const prevImage = () => {
                setCurrentImage((prev) => (prev - 1 + images.length) % images.length);
            };

            return (
                <div className="bg-gray-800 p-8 rounded-xl shadow-lg mb-8 hover-scale transition-transform animate-fadeIn">
                    <h3 className="text-3xl font-bold text-emerald-400">{day}: {title}</h3>
                    <p className="text-gray-400 mt-2"><strong>Distance:</strong> {distance} | <strong>Elevation Gain:</strong> {elevation}</p>
                    <p className="mt-4 text-gray-200">{description}</p>
                    {images && images.length > 0 && (
                        <div className="carousel-container mt-4">
                            <div className="carousel" style={{ transform: `translateX(-${currentImage * 100}%)` }}>
                                {images.map((image, index) => (
                                    <img
                                        key={index}
                                        src={image}
                                        alt={`Scenic view on ${title} ${index + 1}`}
                                        className="route-image"
                                    />
                                ))}
                            </div>
                            {images.length > 1 && (
                                <div className="flex justify-between mt-2">
                                    <button
                                        onClick={prevImage}
                                        className="bg-amber-500 text-gray-900 px-4 py-2 rounded-full hover:bg-amber-400"
                                    >
                                        Prev
                                    </button>
                                    <button
                                        onClick={nextImage}
                                        className="bg-amber-500 text-gray-900 px-4 py-2 rounded-full hover:bg-amber-400"
                                    >
                                        Next
                                    </button>
                                </div>
                            )}
                        </div>
                    )}
                    <p className="mt-4"><strong>Accommodation:</strong> <span className="text-gray-300">{accommodation}</span></p>
                    <p><strong>Dining:</strong> <span className="text-gray-300">{dining}</span></p>
                </div>
            );
        };

        const App = () => (
            <div>
                <Header />
                <main className="container mx-auto py-12 px-4">
                    <section className="mb-16 text-center animate-fadeIn">
                        <h2 className="text-4xl font-bold text-gray-100 mb-6">A Premium 5-Night Bikepacking Adventure</h2>
                        <p className="text-lg text-gray-300 max-w-3xl mx-auto">
                            Indulge in a meticulously curated 250-mile cycling journey through Girona’s breathtaking landscapes. From serene reservoirs to the shimmering Costa Brava, this exclusive tour blends exhilarating rides with luxurious accommodations and gourmet dining. Perfect for discerning cyclists seeking adventure and refinement.
                        </p>
                        <div className="bg-gray-700 h-96 flex items-center justify-center rounded-xl mt-8">
                            <p className="text-gray-400">Interactive Route Map (Integrate with Google Maps or Strava API)</p>
                        </div>
                    </section>
                    <section id="itinerary">
                        <h2 className="text-4xl font-bold text-gray-100 mb-8 text-center">Your Exclusive Itinerary</h2>
                        <ItineraryDay
                            day="Day 1"
                            title="Girona to Sant Vicenç de Torelló"
                            distance="59 miles"
                            elevation="5,800 ft"
                            description={
                                <>
                                    Launch your adventure with the <a href="https://www.strava.com/routes/3337115754495567062" target="_blank" className="text-emerald-400 hover:underline">Strava route</a> from Girona to Sant Vicenç de Torelló. Marvel at the breathtaking beauty of Pantà de Susqueda, where crystalline waters reflect rolling hills and dense forests. This route weaves through smooth roads and light gravel paths, offering a thrilling start to your odyssey.
                                </>
                            }
                            images={["https://drive.google.com/uc?id=106cjVXQ3Zp6AggCV5XXDjoN6pYzhiQIk"]}
                            accommodation="Allotjament Rural Can Passerells - A luxurious rural retreat with cyclist-friendly amenities and serene countryside views."
                            dining="L'Engruna d'en Pousa, Sant Vicenç de Torelló - Savor exquisite Catalan cuisine with a modern twist, featuring local ingredients."
                        />
                        <ItineraryDay
                            day="Day 2"
                            title="Sant Vicenç de Torelló to Banyoles"
                            distance="60 miles"
                            elevation="5,100 ft"
                            description={
                                <>
                                    Embark on an enchanting ride via the <a href="https://www.strava.com/routes/3353945102780710588" target="_blank" className="text-emerald-400 hover:underline">Strava route</a> from Sant Vicenç de Torelló through Olot to the medieval charm of Besalú, and finally to Banyoles. Tackle a thrilling climb through lush, enchanted forests, then pause in Besalú for refreshing gelato and a chilled Coca-Cola amidst its historic stone bridges. Conclude the day cycling around the serene Lake Banyoles, a jewel of Catalonia’s landscape.
                                </>
                            }
                            images={["https://drive.google.com/uc?id=1hWuCsK67SSWBqkKeC3yzhRxFRg0UwCGz"]}
                            accommodation="Casa Maui - A boutique, cyclist-friendly haven with serene lake proximity and premium amenities."
                            dining="Petrichor Banyoles - Indulge in a vibrant fusion of Mediterranean and global flavors, crafted with local ingredients."
                        />
                        <ItineraryDay
                            day="Day 3"
                            title="Banyoles to Tossa de Mar"
                            distance="65 miles"
                            elevation="4,500 ft"
                            description={
                                <>
                                    Begin your day with an exhilarating climb up Rocacorba via this <a href="https://www.strava.com/routes/3353961700586557486" target="_blank" className="text-emerald-400 hover:underline">Strava route</a>, a legendary ascent offering panoramic views. Refuel in Banyoles at Menuda with world-class pastries and coffee, then pedal toward the Costa Brava via this <a href="https://www.strava.com/routes/3338319789874276566" target="_blank" className="text-emerald-400 hover:underline">Strava route</a>. The descent to Tossa de Mar unveils stunning Mediterranean vistas, setting the stage for a coastal evening.
                                </>
                            }
                            images={[
                                "https://drive.google.com/uc?id=19DCnOADhTvE9uUVhg-XrENKzw7RBuLpR",
                                "https://drive.google.com/uc?id=1rLeIYb4vrubglMghdrJsv-6uKqMr2uoh"
                            ]}
                            accommodation="Hotel Diana - A boutique beachfront escape with secure bike storage and oceanfront suites."
                            dining="L'Art Restaurante Port de Reig - Relish classic patatas bravas and authentic paella by the coast."
                        />
                        <ItineraryDay
                            day="Day 4"
                            title="Tossa de Mar to Lloret de Mar"
                            distance="45 miles"
                            elevation="2,500 ft"
                            description="Explore the rugged Costa Brava with a scenic coastal ride, weaving through charming villages and quiet backroads. This shorter day offers time to relax and soak in the Mediterranean ambiance."
                            accommodation="Hotel Rosamar - A luxurious seaside retreat with cyclist-friendly amenities and stunning sea views."
                            dining="Restaurant Sa Caleta, Lloret de Mar - Enjoy fresh seafood and local wines with oceanfront views."
                        />
                        <ItineraryDay
                            day="Day 5"
                            title="Lloret de Mar to Girona"
                            distance="49 miles"
                            elevation="2,900 ft"
                            description="Complete your journey with the iconic Els Àngels climb, followed by serene backroads and coastal vistas. Return to Girona in triumph, ready to celebrate your adventure."
                            accommodation="Hotel Carlemany - A luxurious, cyclist-centric hotel with bike wash stations and premium amenities."
                            dining="La Fabrica, Girona - A cyclist’s favorite, offering exquisite coffee and handcrafted pastries."
                        />
                    </section>
                    <section className="text-center mt-12">
                        <a
                            href="https://x.ai/grok"
                            className="inline-block bg-amber-500 text-gray-900 font-semibold py-4 px-8 rounded-full hover:bg-amber-400 transition hover-scale text-lg"
                        >
                            Book Your Premium Adventure Now
                        </a>
                    </section>
                </main>
                <footer className="bg-gray-950 text-gray-400 py-8">
                    <div className="container mx-auto text-center">
                        <p>© 2025 Girona Luxe Bikepacking Escape. Crafted with passion for elite cyclists.</p>
                        <p className="mt-2 text-sm">Powered by Tailwind CSS and React.</p>
                    </div>
                </footer>
            </div>
        );

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
